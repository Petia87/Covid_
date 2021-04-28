<template>
  <div class="body">
    <TheHeadH1 v-bind:country="country" />
    <CurrentDate />
    <BlueBoxContainer />
    <TextArea @selectedCountry="onSelectedCountry" />
  
  </div>
</template>

<script>
import TheHeadH1 from "./TheHeadH1.vue";
import CurrentDate from "./CurrentDate.vue";
import BlueBoxContainer from "./BlueBoxContainer.vue";
import TextArea from "./TextArea.vue";


export default {
  name: "ThePage",
  components: {
    TheHeadH1,
    CurrentDate,
    BlueBoxContainer,
    TextArea,
   
  },
  methods: {
    onSelectedCountry(country) {
      this.country = country;
    },
  },
  data: function () {
    return {
      country: "",
    };
  },
};
</script>

<style>
.body {
  background: rgb(200, 193, 193);
  background: linear-gradient(
    0deg,
    rgba(200, 193, 193, 1) 0%,
    rgba(255, 255, 255, 1) 44%
  );
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#c8c1c1",endColorstr="#ffffff",GradientType=1);
}
</style>
