<script>
export default {
  data() {
    return {
      tab: 'all',
      textEvent:'',
      eventArr: [
        {
          id: 1,
          check: false, //uncheck
          event: '123',
          editText: '',
        },
        {
          id: 2,
          check: true, //check
          event: '456',
          editText: '',
        }
      ]
    }
  },
  methods: {
    addEvent(){
      const text = this.textEvent;
      const id = this.eventArr.length;
      if (text && text.trim() === '') {
            alert("DON'T PUT BLANK SPACE!");
            this.textEvent = '';  //清空輸入欄的值
          }else if (text != '' || typeof(text) != 'string') {
                const addArr = {
                    id: id + 1,
                    check: 0,
                    event: text,
                    editText: '',
                }
                this.eventArr.push(addArr);
                this.textEvent = ''; 
            } else {
                alert("Don't forget to write down your new event!");
            };
    },
    delItem(id){
                // this.tableArr.pop(index)
                this.eventArr.splice(id, 1)
            },
    editText(id) {
            const content = prompt('Edit event!');
            if (content != '') {
              console.log(content);
              // console.log(item.id);
            const event = this.eventArr[id]; // Get the event object from eventArr using id
            event.event = content; // Update the event content  
    }
        }            
  },
  computed: {
    finishedEvents() {
      return this.eventArr.filter(item => item.check);
    },
    unfinishedEvents(){
    return this.eventArr.filter(item => !item.check);
  }
  },
}
</script>

<template>
  <main class="w-full h-screen bg-pink-200">
    <nav class="w-full h-9 nav-all grid bg-gray-200 absolute">
      <div class="logo w-1/6 text-center flex items-center justify-center">CheckList</div>
    </nav>
    <div class="w-full h-screen flex justify-start items-center flex-col bg-gray-400">
      <div class="search mt-12 w-2/3 flex justify-center items-center">
       
       <input type="text" placeholder="Create Event" class="w-full p-2 add-event-text" v-model="textEvent" />
        <button class="add-event to-do-btn p-2 bg-gray-500 hover:bg-sky-300" @click="addEvent()">Create</button>
      </div>
      <div class="title-all mt-8 w-3/5 flex justify-start">
        <button
          class="title color-change w-[100px] p-2 text-black text-center bg-gray-100 focus:bg-blue-200"
          data-title="All"
          @click="tab = 'all'"
        >
          All
        </button>
        <button
          class="title w-[100px] p-2 text-center text-black bg-gray-200 focus:bg-blue-200"
          data-title="Finish"
          @click="tab = 'finish'"
        >
          Finish
        </button>
        <button
          class="title w-[100px] p-2 text-center text-black bg-gray-300 focus:bg-blue-200"
          data-title="Unfinish"
          @click="tab = 'unfinish'"
        >
          Unfinish
        </button>
      </div>
      <div class="content-all w-full flex justify-center">
        <div class="content w-3/5 flex justify-center flex-col">
          <div class="list-name w-full flex justify-start">
            <div class="w-1/6 p-2">Check</div>
            <div class="w-4/6 p-2">Event</div>
            <div class="w-1/6 p-2 text-center">Function</div>
          </div>
          <ul class="list-item-ul bg-white w-full p-1" v-if="tab == 'all'">
            <ol class="flex p-2 mb-1" v-for="(item, id) in eventArr" :key="id">
              <div class="input-div w-1/6 flex items-center">
                <input type="checkbox" class="check-box" v-model="item.check" @click="" />
              </div>
              <div class="event w-4/6 flex items-center text-black">{{ item.event }}</div>
              <div class="btn-all w-1/6 flex justify-end gap-2">
                <button class="w-1/2 bg-slate-400 rounded p-1 hover:bg-sky-200" @click="editText(id)">Edit</button>
                <button class="w-1/2 bg-slate-200 rounded hover:bg-sky-300" @click="delItem(id)">Delete</button>
              </div>
            </ol>
          </ul>
        <div class="content bg-white w-full p-1  " v-if="tab == 'finish'">
          <ol class="flex p-2 mb-1" v-for="(item, id) in finishedEvents" :key="id" >
              <div class="input-div w-1/6 flex items-center">
                <input type="checkbox" class="check-box" v-model="item.check" @click="" />
              </div>
              <div class="event w-4/6 flex items-center text-black">{{ item.event }}</div>
              <div class="btn-all w-1/6 flex justify-end gap-2">
                <button class="w-1/2 bg-slate-400 rounded p-1 hover:bg-sky-200" @click="editText(id)">Edit</button>
                <button class="w-1/2 bg-slate-200 rounded hover:bg-sky-300" @click="delItem(id)">Delete</button>
              </div>
            </ol>
        </div>  
        <div class="content  bg-white w-full p-1  " v-if="tab == 'unfinish'">
          <ol class="flex p-2 mb-1" v-for="(item, id) in unfinishedEvents" :key="id" >
              <div class="input-div w-1/6 flex items-center">
                <input type="checkbox" class="check-box" v-model="item.check" @click="" />
              </div>
              <div class="event w-4/6 flex items-center text-black">{{ item.event }}</div>
              <div class="btn-all w-1/6 flex justify-end gap-2">
                <button class="w-1/2 bg-slate-400 rounded p-1 hover:bg-sky-200" @click="editText(id)">Edit</button>
                <button class="w-1/2 bg-slate-200 rounded hover:bg-sky-300" @click="delItem(id)">Delete</button>
              </div>
            </ol>
        </div>                
        </div>


      </div>
    </div>
  </main>
</template>
