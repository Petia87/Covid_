<template>
  <div class="main">
    <BlueBox title="Death" count="0"  total=111 />
     <BlueBox title="Cases" count="0"  total=939 />
      <BlueBox title="Death" count="0"  total=111 />
   
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
