<template>
  <select
    v-model="selectedCountry"
    @change="onChange"
    name="countries"
    class="countries"
  >
    <option
      v-for="country in countries"
      :key="country"
      v-bind:value="country.Slug"
    >
      {{ country.Country }}
      <!-- v-bind country да не е стринг а променлива-->
    </option>
  </select>
  {{ selectedCountry }}
  <button @click="onReset" name="countries" class="bcountries">
    Clear Country
  </button>
</template>

<script>
export default {
  name: "TextArea",
 emits: ["selectedCountry", "resetCountry"],
 data: function () {
    return {
      countries: [],
      selectedCountry: "",
    };
  },
  mounted() {
    const userChoice = window.localStorage.getItem("selectedCountry");
    if (userChoice) {
      this.selectedCountry = userChoice;
      
    }
    this.getCountries();
  },
  methods: {
    onChange() {
      //raise event
      this.$emit("selectedCountry", this.selectedCountry);
    },
    onReset() {
      this.selectedCountry = "";
      this.$emit("resetCountry")
    },
    getCountries() {
      fetch("https://api.covid19api.com/countries")
        .then((respons) => {
          return respons.json();
        })
        .then((result) => {
          this.countries = result;
        });
    },
  },
};
</script>


<style scoped>
.countries {
  display: block;
  width: 80%;
  padding: 0.5rem;
  display: block;
  margin: 0 auto;
}
button {
  display: inline-block;
  margin-top: 1rem;
  margin-left: -30rem;
  padding: 0.5rem 0.1rem;
  background: rgb(68, 132, 123);
  color: white;
  margin-bottom: 10rem;
}
</style>
