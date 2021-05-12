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
      //here we can save the selected country in localstorage
      window.localStorage.setItem("selectedCountry", this.selectedCountry);
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
 box-shadow: 6px 6px 5px -2px rgba(31,26,26,0.2);
-webkit-box-shadow: 6px 6px 5px -2px rgba(31,26,26,0.2);
-moz-box-shadow: 6px 6px 5px -2px rgba(31,26,26,0.2);
}
@media(max-width: 675px){
  .bcountries{
    margin-left: 0rem;
    
  }
}
</style>
