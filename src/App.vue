<template>
<TheHeader/>
  <ThePage/>
 

</template>

<script>
import TheHeader from './components/TheHeader.vue'
import ThePage from './components/ThePage.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    ThePage
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
body,div{
  margin: 0;
  padding: 0;
}
</style>
