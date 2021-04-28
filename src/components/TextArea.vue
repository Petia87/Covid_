<template>
<select name="city" class="city">
<option value="vue-result">{{result}}</option>

 </select>
 

</template>

<script>
export default {
  name: "TextArea",
  props: {},
  
}
  
</script>


<style scoped>
.city{
  width: 80%;
  padding: 0.5rem;
 display: block;
 margin: 0 auto;
}
</style>
