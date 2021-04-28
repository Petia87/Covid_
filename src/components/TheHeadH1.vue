<template>
  <h1>{{city}}</h1>
</template>

<script>
export default {
  name: "TheHeadH1",
  props: ["city"],
}
</script>


<style scoped>
h1 {
  padding: 0.3rem;
  font-weight: 900;
  font-size: 1.4rem;
  margin: 0;
}

</style>
