<template>
  <div class="event-page">
    <div class="event-details">
      <EventCard v-if='this.event' v-bind:myEvents="event" />
      <div class="event-details-side">
        <Attendeess />
        <EventMiniMap />
      </div>
    </div>
  </div>
</template>


<script>
import EventCard from "./EventCard"
import Attendeess from "./Attendeess"
import EventMiniMap from "./EventMiniMap"

export default {
  name: 'EventById',
  components: {
    EventCard,
    Attendeess,
    EventMiniMap
  },
  data() {
    return {
      event: null,
      event_id: null
    }
  },
  methods: {
    getEventData() {
      // fetch(`https://openvillage.herokuapp.com/events/${this.event_id}`)
      fetch(`http://localhost:9000/events/${this.event_id}`)
        .then(response => response.json())
        .then(myData => this.event = myData.event[0])
    },
    getQueryString() {
      let locationName = location.href
      console.log(locationName.split('/'))
      this.event_id = (locationName.split('/')[5])
    }
  },
  mounted() {
    this.getQueryString()
    this.getEventData()
  }
}

</script>

<style scoped>

.event-page {
  background-color: rgb(228, 230, 234);
  padding: 4vw;
}

.event-details {
  display: flex;
}

.event-details-side {
  width: 50vw;
  display: flex;
  flex-direction: column;
  margin-left: 4vw;
}

</style>
