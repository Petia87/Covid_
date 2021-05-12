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
  box-shadow: 6px 8px 5px 0px rgba(31,26,26,0.2);
-webkit-box-shadow: 6px 8px 5px 0px rgba(31,26,26,0.2);
-moz-box-shadow: 6px 8px 5px 0px rgba(31,26,26,0.2);
  }
.covid-status--deaths{
  background: rgb(177, 211, 255);
}


.p1{
  color: blue;
  font-weight:bold;
  padding:0.2rem;
 margin-top: 1rem;
}
.p2{
  font-weight:bold ;
  font-size:0.9rem;
  padding:0.2rem
}
.covid-status__total{
  margin-bottom: 1rem;
}


</style>
