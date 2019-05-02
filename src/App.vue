<template lang="html">
<div>
  <h1>Countries</h1>
  <!-- <countries-list :countries='countries'></countries-list> -->
  <select-view :countries='countries'></select-view>
  <countries-detail :country='selectedCountry'></countries-detail>
</div>


</template>

<script>
import CountriesDetail from './components/CountriesDetail.vue';
import CountriesList from './components/CountriesList.vue';
import SelectView from './components/SelectView.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch("https://restcountries.eu/rest/v2/all")
    .then(res => res.json())
    .then(countries => this.countries = countries);

    eventBus.$on("country-selected", (index) => {
      // this.selectedCountry = this.country
      // changed to line below so select works - because it passes index onto
      //event bus, rather than whole country object
      this.selectedCountry = this.countries[index];
    });
  },
  components: {
    "countries-list": CountriesList,
    "countries-detail": CountriesDetail,
    "select-view": SelectView
  }
}
</script>



<style lang="css" scoped>

</style>
