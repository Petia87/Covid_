<template>
  <div v-if="show" class="backdrop">
    <div class="popup-container">
       <span><i class="fas fa-exclamation-triangle"></i></span>
      {{ message }}

      <button @click="onClose" class="close">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "PopUp",
  props: ["show", "message"],
  emits: ["popupClose"],
  methods: {
    onClose() {
      this.$emit("popupClose");
    },
  },
};
</script>


<style >
/*.backdrop {
  position: fixed;
  background: rgba(187, 184, 184, 0.6);
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}*/
.popup-container {
  background: white;
  position: fixed;
  top: 50%;
  left: 30%;
  padding: 2rem;
  color:red;
  box-shadow: 6px 8px 5px 0px rgba(31,26,26,0.2);
-webkit-box-shadow: 6px 8px 5px 0px rgba(31,26,26,0.2);
-moz-box-shadow: 6px 8px 5px 0px rgba(31,26,26,0.2);

}

.close {
      position: absolute;
    top: 0.5rem;
    right: 0.3rem;
    border-radius: 20%;
    padding: 0.1rem;
    margin-bottom: 0.3rem;
    font-size: 0.7rem;
}
.fa-exclamation-triangle{
color: red;
}
.close{
  background: red;
  color: aliceblue;
}
@media(max-width: 675px){
  .popup-container{
  justify-content: center;
    
  }
}
</style>
