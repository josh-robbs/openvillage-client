<template>
  <ul class="float-list">
    <li class="event-cards" v-for="oneEvent in allEvents" :key="oneEvent.id">
        <b-card :img-src="`${oneEvent.image_url}`"
                img-alt="Image"
                img-top
                tag="article"
                style="max-width: 14rem; max-height: 45rem;"
                class="mb-2">
          <h4 class="card-title">{{oneEvent.name}}</h4>
          <p class="card-text">{{oneEvent.description}}</p>
          <div class="moreButton">
            <router-link :to="`/events/${oneEvent.id}`">Event Details</router-link>
          </div>
          <div class="accent"></div>        
      </b-card>
    </li>
  </ul>
</template>


<script>
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'
  export default {
    name: "EventList",
    props: ["allEvents"]
  }
</script>


<style scoped>
  .float-list {
    position: absolute;
    top: 8vw;
    right: 10vw;
    width: 40vw;
    list-style: none;
        display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    overflow: scroll;
    max-height: 70vh;

  }
  .event-cards p {
    white-space: nowrap; 
    overflow: hidden;
    text-overflow: ellipsis; 
  }

  .event-cards h4 {
    width: inherit;
    height: 3vw;
    white-space: wrap; 
    overflow: hidden;
    text-overflow: ellipsis; 
  }

  .event-cards {
    max-height: 50vh;
  }

  .card-title {
    font-size: 1.5em;
  }

  .moreButton {
    display: flex;
    justify-content: flex-end;
    margin-right: 2vw;
    height: 2vw;
    padding-left: 2vw;
  }
  
</style>