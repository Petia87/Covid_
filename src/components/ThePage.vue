<template>
  <div class="body">
    <TheHeadH1 v-bind:country="country" />
    <CurrentDate />
    <div class="main">
      <BlueBox
        class="blueBox"
        title="Cases"
        v-bind:count="casesCount"
        v-bind:total="totalCasesCount"
      />
      <BlueBox
        class="blueBox"
        title="Deaths"
        v-bind:count="deathsCount"
        v-bind:total="totalDeathsCount"
        isDeaths="true"
      />
    </div>
    <TextArea
      @selectedCountry="onSelectedCountry"
      @resetCountry="onResetCountry"
    />
    <PopUp
      v-bind:show="showPopup"
      @popupClose="closePopup"
      message="No data available for this country"
    />
    <PopUp
      class="server"
      v-bind:show="showError"
      @popupClose="closePopup"
      message="Server is down"
    />
  
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
    
  },
  mounted() {
    //mounted livecycle hook vue го извиква в подходящия момент we can search on array-onselected country

    fetch(`https://api.covid19api.com/summary`)
      .then((response) => {
        return response.json();
      })
      .then((data) => {
         this.countries = data.Countries;
      })
      .catch(() => {
        this.showError = true;
      });
  },

  methods: {
    closePopup() {
      //we close the popup by setting showPopup to false
      this.showPopup = false;
      this.showError = false;
    },
    onResetCountry() {
      this.casesCount = 0;
      this.deathsCount = 0;
      this.totalCasesCount = 0;
      this.totalDeathsCount = 0;
      this.country = "";
    },
    onSelectedCountry(country) {
      //we can save the selected country in the localstorage
      this.casesCount = 0;
      this.deathsCount = 0;
      this.totalCasesCount = 0;
      this.totalDeathsCount = 0;
      this.country = country;

      if (this.country !== "") {
        this.countryObject = this.countries.find((object) => {
          //predicat returs boolean

          return object.Country.toLowerCase() === this.country.toLowerCase();
        });
        if (this.countryObject) {
          this.totalCasesCount = this.countryObject.TotalConfirmed;
          this.totalDeathsCount = this.countryObject.TotalDeaths;
        } else {
          this.totalCasesCount = "n/a";
          this.totalDeathsCount = "n/a";
          this.showPopup = true;
        }
      }
    },
  },

  data: function () {
    return {
      countryObject: {},
      countriesArr: [], //1.create arr
      country: "",
      casesCount: 0,
      deathsCount: 0,
      totalCasesCount: 0,
      totalDeathsCount: 0,
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

@media (max-width: 675px) {
  .main {
    flex-direction: column;
  }
}
</style>
/* //Nina
      if (this.country !== "") {
        fetch(
          `https://api.covid19api.com/summary/${country}`
          //`https://api.covid19api.com/country/${country}/status/confirmed?from=2020-03-01T08:00:00Z&to=2020-03-01T09:00:00Z`
        )
          .then((response) => {
            return response.json(); //decodding the response for js
          })
          .then((data.Countries.find( ({country})) => {
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
            this.showError = true;
          });

        //..............................................
        fetch(
          `https://api.covid19api.com/total/country/${country}/status/confirmed?from=2019-03-01T08:00:00Z&to=2020-03-01T09:00:00Z`
        )
          .then((response) => {
            return response.json(); //decodding the response for js
          })
          .then((totaldate) => {
            if (totaldate.length === 0) {
              this.totalCasesCount = "n/a";
              this.showPopup = true;
            } else {
              this.totalCasesCount = totaldate[0].Cases;
            }
          })
          .catch((error) => {
            console.log(error);
            this.showError = true;
          });

       /* fetch(
          `https://api.covid19api.com/world?from=2020-03-01T00:00:00Z&to=2020-04-01T00:00:00Z`
        )
          .then((response) => {
            return response.json();
          })
          .then((totalanswer) => {
            if (totalanswer.length === 0) {
              this.totalDeathsCount = "n/a";
              this.showPopup = true;
            } else {
              this.totalDeathsCount = totalanswer[0].Cases;
            }
          })
          .catch((error) => {
            console.log(error);
            this.showError = true;
          });*/