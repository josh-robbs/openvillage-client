<template>
  <div class = "form-container">
    <form id="form" @submit.prevent="postNewEvent">
      <div class = "form-div">
        <label htmlFor="name">Organizer Id:</label>
        <input type="integer" name="organizer" v-model="formData.organizer" />
      </div>
      <div class = "form-div">
        <label htmlFor="eventName">Event Name:</label>
        <input type="text" name="eventName" v-model="formData.name" />
      </div>
      <div class = "form-div">
        <label htmlFor="lat">Latitude:</label>
        <input type="integer" name="lat" v-model="formData.lat" />
      </div>
      <div class = "form-div">
        <label htmlFor="long">Longitude:</label>
        <input type= "integer" name="long" v-model="formData.long" />
      </div>
      <div class = "form-div">
        <label htmlFor="description">Description:</label>
        <textarea type="text" name="description" v-model="formData.description">My event is...</textarea>
      </div>
      <div class = "form-div">
        <label htmlFor="start_at">Start time:</label>
        <input type="time" name="start_at" v-model="formData.start_at" />
      </div>
      <div class = "form-div">
        <label htmlFor="end_at">End time:</label>
        <input type="time" name="end_at" v-model="formData.end_at" />
      </div>
      <div class = "form-div">
        <label htmlFor="date">Date:</label>
        <input type="date" name="date" v-model="formData.date" />
      </div>
      <div class = "form-div">
        <label htmlFor="image_url">Image URL:</label>
        <input type="image_url" name="image_url" v-model="formData.image_url" />
      </div>
      <input id="submit-button" type="submit" name="submit" value="Submit" />
    </form>
  </div>
</template>


<script>
export default {
  name: 'Form',
  data(){
    return {
      formData: {
        organizer: '',
        name: '',
        lat: '',
        long: '',
        description: '',
        start_at: '',
        end_at: '',
        date: '',
        image_url: ''
      }
    }
  },
  methods: {
    postNewEvent(){
      fetch('https://openvillageapp.herokuapp.com/events', {
      // fetch('http://localhost:9000/events', {
        method: 'POST',
        headers: { "content-type": "application/json" },
        body: JSON.stringify(this.formData)
      })
    }
  }
}
</script>


<style>
#form {
  display:flex;
  flex-direction:column;
  padding:1vw;
  width:40vw;
  align-items:center;
}
.form-div {
  padding:1vw;
}
input {
  width: 40vw;
}
textarea {
  width: 40vw;
}
.form-container {
  display:flex;
  justify-content:center;
  background-color: rgb(228, 230, 234);
}
#submit-button {
  padding: 1vw;
  width: 20vw;
}
</style>