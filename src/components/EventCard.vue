<template>
  <div class="event-card">
    <img class="event-image" :src="`${this.myEvents.image_url}`" alt="">
    <div class='event-info'>
      <h2>{{this.myEvents.name}}</h2>
      <h3>Event Date: {{this.myEvents.date}}</h3>
      <h3>Time: {{this.myEvents.start_at}} to {{this.myEvents.end_at}}</h3>
      <h4>Organizer: {{this.myEvents.firstname}} {{this.myEvents.lastname}}</h4>
      <p>Description: {{this.myEvents.description}}</p>
    </div>
    <button @click="this.deleteEvent" id="delete" type="button" name="button">Delete</button>
  </div>
</template>

<script>
export default {
  name: "EventCard",
  props: ['myEvents'],
  methods: {
    deleteEvent (event) {
      const event_id = event.target.id
      // fetch(`https://openvillage.herokuapp.com/events/${this.myEvents.id}`, {
      fetch(`http://localhost:9000/events/${this.myEvents.id}`, {
        method: 'DELETE'
      })
    }
  }
}
</script>

<style scoped>

.event-card {
  display: flex;
  flex-direction: column;
  background-color:rgb(232, 245, 252);
  color: black;
  text-align: center;
  text-decoration: none;
  font-size: 1vw;
  /* height: 40vw; */
  width: 30vw;
  border-radius: .25vw;
  border: 1px solid black;
  box-shadow: .06vw .06vw .06vw 0vw rgba(0,0,0,0.75);
}
.event-info {
  display: flex;
  flex-direction: column;
  padding: .5vw;
  align-items: center;
}

.event-info h2 {
  padding: .5vw;
  width: 20vw;
}

.event-info h3 {
  font-size: 1vw;
}

.event-info p {
  padding: .5vw;
  width: 20vw;
}

.event-image {
  height: 40vh;
}


#delete {
  margin-left: 13vw;
  margin-bottom: 1vw; 
  font-size: 0.8vw;
  width: 4vw;
  height: auto;
}
</style>