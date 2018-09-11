<template>
  <div class='about-page'>
    <h1>About Open Village</h1>
    <p>Open Village is an application created to help motivated communities simplify their community service initatives
      by providing a platform where neighhbors can advertise upcoming community service events, communicate with attendees
      and set times and places for events.
    </p>
    <ul class="staff-cards">
      <StaffCard v-for = "member in members" :key="member.id" :member = "member"/>
    </ul>

  </div>
</template>


<script>
import StaffCard from "./StaffCard"

export default {
  name: 'About',

  components: {
    StaffCard
  },

  data(){
    return {
      members: []
    }
  },

  methods: {
  getMembers() {
    // fetch("https://openvillage.herokuapp.com/neighbors")
    fetch('http://localhost:9000/neighbors')
      .then(response => response.json())
      .then(myData => this.members = (myData.event))
    }
  },

  mounted(){
    this.getMembers()
  }
}
</script>


<style scoped>
.about-page {
  margin: 6vw 4vw 15.5vw 4vw;
}

.staff-cards {
  display: flex;
  list-style: none;
  justify-content: space-around;
  margin-top: 4vw;
}


</style>
