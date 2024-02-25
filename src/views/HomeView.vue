<script setup>

</script>

<template>
  <main class="w-full h-screen bg-pink-200 ">
    <nav class="w-full h-9 nav-all grid bg-gray-200 absolute">
      <div class="logo w-1/6 text-center flex items-center justify-center ">CheckList</div>
    </nav>
    <div class="w-full h-screen flex justify-start items-center flex-col bg-gray-400">
      <div class="search mt-12 w-2/3 flex justify-center items-center ">
        <input type="text" placeholder="Create Event" class="w-full p-2 add-event-text">
        <button class="add-event to-do-btn p-2 bg-gray-500 hover:bg-sky-300">Create</button>
      </div>
      <div class="title-all mt-8 w-3/5 flex justify-start">
        <button class="title color-change w-[100px] p-2 text-center bg-gray-100 focus:bg-blue-200 "
          data-title="All">All</button>
        <button class="title w-[100px] p-2 text-center bg-gray-200 focus:bg-blue-200" data-title="Finish">Finish</button>
        <button class="title w-[100px] p-2 text-center bg-gray-300 focus:bg-blue-200"
          data-title="Unfinish">Unfinish</button>
      </div>
      <div class="content-all w-full flex justify-center">
        <div class="content w-3/5 flex justify-center flex-col" data-content="All">
          <div class="list-name w-full flex justify-start">
            <div class="w-1/6 p-2">Check</div>
            <div class="w-4/6 p-2">Event</div>
            <div class="w-1/6 p-2 text-center ">Function</div>
          </div>
          <ul class="list-item-ul bg-white w-full p-1">
            <ol class="flex p-2 mb-1">
              <div class="input-div w-1/6 flex items-center">
                <input type="checkbox" onclick="CheckOrNot(${item.id})" class="check-box">
              </div>
              <div class="event w-4/6 flex items-center">${item.text}</div>
              <div class="btn-all w-1/6 flex justify-end gap-2">
                <button onclick="editText(${item.id})"
                  class="w-1/2 bg-slate-400 rounded p-1 hover:bg-sky-200">Edit</button>
                <button onclick="deleteText(${item.id})"
                  class="w-1/2 bg-slate-200 rounded hover:bg-sky-300 ">Delete</button>
              </div>
            </ol>
            <ol class="flex p-2 mb-1">
              <div class="input-div w-1/6 flex items-center">
                <input type="checkbox" onclick="CheckOrNot(${item.id})" class="check-box">
              </div>
              <div class="event w-4/6 flex items-center">${item.text}</div>
              <div class="btn-all w-1/6 flex justify-end gap-2">
                <button onclick="editText(${item.id})"
                  class="w-1/2 bg-slate-400 rounded p-1 hover:bg-sky-200">Edit</button>
                <button onclick="deleteText(${item.id})"
                  class="w-1/2 bg-slate-200 rounded hover:bg-sky-300">Delete</button>
              </div>
            </ol>
          </ul>

        </div>
        <div class="content hidden" data-content="Finish">
        </div>
        <div class="content hidden" data-content="Unfinish"></div>
      </div>

  </div>
</main></template>
