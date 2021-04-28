<template>
  <select @change="onChange" name="countries" class="countries">
    <option v-for="country in countries" :key="country" v-bind:value="country">
      {{ country }}
      <!-- v-bind country да не е стринг а променлива-->
    </option>
  </select>
  <button @click="onClick" name="countries" class="countries">
  Clear Country
</button>
</template>

<script>
import { countryList } from "../data/countries.js";

export default {
  name: "TextArea",
  data: function () {
    //функция връщаш обект
    return {
      countries: countryList, // Вътрешни пропъртита за този обект
      selectedCountry: "",
    };
  },
  mounted() {
    // console.log(countryList); Принтират се държави в конзолата
  },
  methods: {
    onChange(eventInfo) {
      this.selectedCountry = eventInfo.target.value;
      //запазваме селектирната държава в паметта на компонента като създаваме вараябъл в дата ,която пази селект. държава
    //raise event
    this.$emit("selectedCountry", this.selectedCountry)
    },
     onClick() {
      this.selectedCountry = "";
      this.$emit("selectedCountry", this.selectedCountry);
    },
 
  },
};
</script>


<style scoped>
.city {
  display: block;
  width: 80%;
  padding: 0.5rem;
  display: block;
  margin: 0 auto;
}
button{
  display: inline;
  margin-top:1rem ;
  margin-left: -30rem;
  padding: 0.5rem 0.1rem;
  background: rgb(68, 132, 123);
  color:white ;
  margin-bottom:10rem;
}
</style>
