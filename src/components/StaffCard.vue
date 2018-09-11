<template>
  <li class='staff-info'>
    <p>{{member.firstname}} {{member.lastname}}</p>
    <img class='member-image' :src="`${member.image}`" :alt="`Image of `+`${member.firstname}`+` `+`${member.lastname}`">
  </li>
</template>


<script>
  export default {
    name:"StaffCard",
    props: ["member"]
  }
</script>


<style scoped>
  .member-image {
    width: 15vw;
    height: 15vw;
    border-radius: 100%;
    background-color: gray;
  }
  .staff-info {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
