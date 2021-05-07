<template>
  <div>{{ currentDate }}</div>
</template>

<script>
import moment from "moment";
export default {
  name: "CurrentDate",
  props: {},
  data: function () {
    return {
      currentDate: "",
    };
  },
   created() {
      this.getNow();
    this.currentDate = this.getCurrentDateTime();
    },
  methods: {
    getCurrentDateTime() {
      return moment().format("MMMM Do YYYY HH:mm:ss");
    },
   
    getNow: function () {
      const current = new Date();
      const date = `${[current.getMonth() + 1]} ${current.getDate()} ${current.getFullYear()}`;
      const time = `${current.getHours()}:${current.getMinutes()}:${current.getSeconds()}`;
      const dateTime = date + " " + time;
      this.currentDate = dateTime
    },
  },
};
</script>


<style scoped>
div {
  font-size: 1rem;
  margin: 0;
  padding: 0;
}
</style>
