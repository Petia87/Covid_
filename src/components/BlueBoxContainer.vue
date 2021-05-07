<template>
  <div class="main">
    <BlueBox title="Death" v-bind:count="casesCount"  total="" />
    <BlueBox title="Cases" v-bind:count="deathsCount" total="" isDeaths="true"/>
   
   
  </div>
</template>

<script>
import BlueBox from "./BlueBox.vue";
export default {
  name: "BlueBoxContainer",
  components: {
    BlueBox,
  },
};
</script>


<style scoped>
.main {
  display: flex;
  justify-content: space-around;
  margin: 2rem;
}
</style>
