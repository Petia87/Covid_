<template>

  <div class="first covid-status" v-bind:class="{ 'covid-status--deaths': isDeaths }">
    <p class="p1 covid-status__title">{{title}}</p>
    <p class="p2 covid-status__count">New:{{count}}</p>
    <p class="p2 covid-status__total">Total:{{total}}</p>
  </div>

  
</template>

<script>
export default {
  name: "BlueBox",
  props: ["title","count", "total","isDeaths"],
  }
 

  
</script>


<style scoped>

.covid-status{
width: 100%;
margin: 0.5rem;
}

.covid-status{
   background: rgb(208, 228, 253);
  }
.covid-status--deaths{
  background: rgb(177, 211, 255);
}


.p1{
  color: blue;
  font-weight:bold;
}
.p2{
  font-weight:bold ;
}
</style>
