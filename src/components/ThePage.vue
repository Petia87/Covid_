<template>
  <div class="body">
    <TheHeadH1 v-bind:country="country" />
    <CurrentDate />
    <div class="main">
    <BlueBox title="Death" v-bind:count="casesCount" total="" />
    <BlueBox title="Cases" v-bind:count="deathsCount" total="" isDeaths="true"
    />
  </div>
    <TextArea
      @selectedCountry="onSelectedCountry"
      @resetCountry="onResetCountry"
    />
    <PopUp>
      v-bind:show="showPopup"
      @popupClose="closePopup"
      message="No data available for this country"
    <PopUp/>
    <PopUp>
      v-bind:show="showError"
      @popupClose="closePopup"
      message="Server is down"
   <PopUp/>
  </div>
</template>

<script>
import TheHeadH1 from "./TheHeadH1.vue";
import CurrentDate from "./CurrentDate.vue";
import BlueBox from "./BlueBox.vue";
import TextArea from "./TextArea.vue";
import PopUp from "./PopUp.vue";

export default {
  name: "ThePage",
  components: {
    TheHeadH1,
    CurrentDate,
    BlueBox,
    TextArea,
    PopUp,
  },//Nina
  methods: {
    closePopup() {
      //we close the popup by setting showPopup to false
      this.showPopup = false;
      this.showError = false;
    },
    onResetCountry() {
      this.casesCount = 0;
      this.deathsCount = 0;
      this.country = "";
    },
    onSelectedCountry(country) {
      //we can save the selected country in the localstorage
      this.casesCount = 0;
      this.deathsCount = 0;
      this.country = country;
//Nina
       if (this.country !== "") {
        fetch(
          `https://api.covid19api.com/country/${country}/status/confirmed?from=2020-03-01T08:00:00Z&to=2020-03-01T09:00:00Z`
        )
          .then((response) => {
            return response.json(); //decodding the response for js
          })
          .then((data) => {
            if (data.length === 0) {
              this.casesCount = "n/a";
              this.showPopup = true;
            } else {
              this.casesCount = data[0].Cases;
              console.log(this.country, this.casesCount);
            }
          })
          .catch((error) => {
            console.log(error);
            this.showError = true;
          });

        fetch(
          `https://api.covid19api.com/country/${country}/status/deaths?from=2020-03-01T08:00:00Z&to=2020-03-01T09:00:00Z`
        )
          .then((response) => {
            return response.json();
          })
          .then((answer) => {
            if (answer.length === 0) {
              this.deathsCount = "n/a";
              this.showPopup = true;
            } else {
              this.deathsCount = answer[0].Cases;
              console.log(this.country, this.deathsCount);
            }
          })
          .catch((error) => {
            console.log(error);
            this.showError = true; //we change this in 10places?
          });
      }
    },
  },
  

  data: function () {
    return {
      country: "",
      casesCount: 0,
      deathsCount: 0,
      showPopup: false,
      showError: false,
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
.main {
  display: flex;
  justify-content: space-around;
  margin: 2rem;
}
</style>
