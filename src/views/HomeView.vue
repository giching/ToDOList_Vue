<script setup>

</script>

<template>
  <main class="container bg-inherit">
    <nav class="nav-all">
        <div class="logo col-2">CheckList</div>
    </nav>
    <div class="mybody">
        <div class="search">
            <input type="text" placeholder="Create Event" class="col-10 add-event-text">
            <button class="add-event to-do-btn col-2">Create</button>
        </div>
        <div class="title-all">
            <div class="title color-change" data-title="All">All</div>
            <div class="title" data-title="Finish">Finish</div>
            <div class="title" data-title="Unfinish">Unfinish</div>
        </div>
        <div class="content-all">
            <div class="content" data-content="All">
                <div class="list-name row">
                    <div class="col-1">Check</div>
                    <div class="col-9">Event</div>
                    <div class="col-2">Function</div>
                </div>
                <ul class="list-item-ul">
                </ul>

            </div>
            <div class="content hidden" data-content="Finish">
            </div>
            <div class="content hidden" data-content="Unfinish"></div>
        </div>

    </div>
  </main>
</template>
