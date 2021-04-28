<template>

  <div class="first">
    <p class="p1">{{title}}</p>
    <p class="p2">New:{{count}}</p>
    <p class="p2">Total:{{total}}</p>
  </div>

  
</template>

<script>
export default {
  name: "BlueBox",
  props: ["title","count", "total"],
  }
 

  
</script>


<style scoped>

.first{
width: 100%;
margin: 0.5rem;
}
.first{
 
  background: rgb(212, 230, 254);
  
}

.p1{
  color: blue;
  font-weight:bold;
}
.p2{
  font-weight:bold ;
}
</style>
