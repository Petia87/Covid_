<template>
  <div v-if="show" class="backdrop">
    <div class="popup-container">
      {{massage}}
 <button @click="onClose" class="close">Close</button>
    </div>
     </div>
</template>

<script>
export default {
  name: "PopUp",
  props: ["show","massage"],
  emits: ["popupClose"],
  methods: {
    onClose() {
      this.$emit("popupClose");
    },
  },
};
</script>


<style >
.backdrop {
  position: fixed;
  background: rgba(187, 184, 184, 0.6);
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}
.popup-container {
  background: grey;
  position: fixed;
  top: 50%;
  left: 30%;
  padding: 2rem;
  color: aliceblue;
}

.close {
  position: absolute;
  bottom: 11.9rem;
  margin: 0.5rem 0;
  left: 23rem;
}
</style>
