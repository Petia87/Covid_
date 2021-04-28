<template>
  <div>{{ currentDate() }}</div>
</template>

<script>
export default {
  name: "BlueBox",
  props: {},
  methods: {
    currentDate() {
      const current = new Date();
      var months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      const date = `${
        months[current.getMonth() + 1]
      } ${current.getDate()}st ${current.getFullYear()}`;
      const time = `${current.getHours()}:${current.getMinutes()}:${current.getSeconds()}pm`;
      const dateTime = date + " " + time;
      return dateTime;
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
