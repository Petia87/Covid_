<template>
  <div class="body">
    <TheHeadH1 v-bind:country="country" />
    <CurrentDate />
    <BlueBoxContainer />
    <TextArea
      @selectedCountry="onSelectedCountry"
      @resetCountry="onResetCountry"
    />
    <PopUp
      v-bind:show="showPopup"
      @popupClose="closePopup"
      massage="No data available for this country"
    />
    <PopUp
      v-bind:show="showError"
      @popupClose="closePopup"
      massage="Serve is down"
          />
             <!-- v-bind - in order to accept it as varaible, not string -->
  </div>
</template>

<script>
import TheHeadH1 from "./TheHeadH1.vue";
import CurrentDate from "./CurrentDate.vue";
import BlueBoxContainer from "./BlueBoxContainer.vue";
import TextArea from "./TextArea.vue";
import PopUp from "./PopUp.vue";

export default {
  name: "ThePage",
  components: {
    TheHeadH1,
    CurrentDate,
    BlueBoxContainer,
    TextArea,
    PopUp,
  },
  methods: {
    closePopup() {
      this.showPopup = false;
      this.showError = false;
    },
    onResetCountry() {
      this.country = "";
      this.casesCount = 0;
      this.deathsCount = 0;
    },
    onSelectedCountry(country) {
      this.country = country;
      this.casesCount = 0;
      this.deathsCount = 0;
      if (this.country !== "") {
        fetch(
          `https://api.covid19api.com/country/${country}/status/confirmed?from=2020-03-01T08:00:00Z&to=2020-03-01T09:00:00Z`
        )
          .then((response) => {
            return response.json();
          })
          .then((data) => {
            if (data.length === 0) {
              this.casesCount = "n/a";
              this.showPopup = true;
            } else {
              this.casesCount = data[0].Cases;
             console.log(this.country, this.casesCount);
              this.deathsCount = answer[0].Cases;
              console.log(this.country, this.deathsCount);
            }
          })
          .catch(() => {
            this.showError = true;
            this.showPopup = true;
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
</style>
