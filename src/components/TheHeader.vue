<template>

<header class="header">
  <h1>
 <span><i class="fas fa-virus"></i></span>
 Covid-19 Tracker
 </h1>
<p><span class="api"> APi by</span>
  covid19api.com</p>



</header>

  
</template>

<script>
export default {
  name: 'TheHeader',
  props: {
  }
}
</script>


<style scoped>
.header{
 background:rgb(24, 59, 165);
 padding: 0.5rem;
}
h1,p{
margin: 0.3rem;
  color: aliceblue;
}
.api{
  font-weight: bold;
}
.fas{
  size: 0.5rem;
 padding-right: 3px;
}
p{
  font-size: 0.5rem;
}


</style>
