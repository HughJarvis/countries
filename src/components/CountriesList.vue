<template lang="html">
  <div>
    <!-- <h1>Countries List</h1> -->
    <div class="countries-list">
      <ul>
        <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item>
      </ul>
    <!-- <label for="country-select">Select Country</label>
    <select id="country-select" v-model="selectedCountry">
      <option disabled value="">Select country</option>
      <option v-for="(country, index) in countries" :value="country">{{country.name}}</option>
    </select> -->
    </div>
  </div>
</template>

<script>
import ListItem from './ListItem';

export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
.countries-list {
  height: 400px;
  overflow: scroll;
  background-color: lightblue;
}
</style>
