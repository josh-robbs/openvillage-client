<template>
  <div class="attendee-container">
    <h1>Attending:</h1>
    <div class="attendee-list">
      <div class="attendee-card">
        <img src="http://a.espncdn.com/combiner/i?img=/i/headshots/nfl/players/full/16735.png&w=350&h=254" alt="attendee image">
      </div>
      <div class="attendee-card">
        <img src="http://a.espncdn.com/combiner/i?img=/i/headshots/nfl/players/full/8439.png&w=350&h=254" alt="attendee image">
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: 'Attendeess',
  data() {
    return {
      event_id: null
    }
  },
  methods: {
    // getEventData() {
    //   fetch(`https://openvillage.herokuapp.com/events/${this.event_id}`)
    //   fetch(`http://localhost:9000/events/${this.event_id}`)
    //   What is this path and route? Need to write
    //     .then(response => response.json())
    //     .then(myData => this.event = myData.event[0])
    // },
    // getQueryString() {
    //   let locationName = location.href
    //   console.log(locationName.split('/'))
    //   this.event_id = (locationName.split('/')[5])
    // }
  }
}

</script>


<style scoped>
.attendee-container {
  display: flex;
  flex-direction: column;
  width: 50vw;
  margin-bottom: 2vw;
  padding: 1vw;
  background-color: lightblue;
  box-shadow: .06vw .06vw .06vw 0vw rgba(0,0,0,0.75);
  border-radius: .25vw;


}

.attendee-list {
  display: flex;
  
}

.attendee-card {
  background-color: white;
  margin: 1vw;
  border-radius: 100%;
  
}

.attendee-card img, h2 {
  font-size: 1vw;
  height: 4vw;
  width: 4vw;
  border-radius: 100%;
  

}

</style>
