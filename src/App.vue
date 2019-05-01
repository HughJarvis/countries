<template lang="html">
<div>
  <h1>Countries</h1>
  <countries-list :countries='countries'></countries-list>
  <countries-detail :country='selectedCountry'></countries-detail>
</div>


</template>

<script>
import CountriesDetail from './components/CountriesDetail';
import CountriesList from './components/CountriesList';
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

    eventBus.$on("country-selected", (country) => {
      this.selectedCountry = country;
    });
  },
  components: {
    "countries-list": CountriesList,
    "countries-detail": CountriesDetail
  }
}
</script>



<style lang="css" scoped>

</style>
