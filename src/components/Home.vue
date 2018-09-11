<template>
  <div>
    <GoogleMap v-if='this.allEvents' v-bind:allEvents="allEvents"/>
    <EventList v-bind:allEvents="allEvents" />
  </div>
</template>


<script>
import EventList from './EventList'
import GoogleMap from './GoogleMap'

export default {
  name: 'App',
  components: {
    GoogleMap,
    EventList
  },
  data(){
    return {
      allEvents: null
    }
  },
  methods: {
    getData(){
      fetch('https://openvillageapp.herokuapp.com/events')
      // fetch('http://localhost:9000/events')
        .then(response => response.json())
        .then(myData => this.allEvents = myData.event)
    }
  },
  mounted() {
    this.getData()
  }
}
</script>


<style>

</style>