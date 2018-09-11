<template>
  <b-navbar toggleable="md" type="dark" variant="info">
    <b-navbar-brand class="footer-text" href="#">
      <small>&copy; TacoCorp 2018</small>
    </b-navbar-brand>
  </b-navbar>
</template>


<script>
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'

  export default {
    name: 'Footer'
  }
</script>


<style scoped>
  .footer-text {
    display: flex;
    justify-content: center;
  }
</style>