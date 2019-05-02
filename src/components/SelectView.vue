<template lang="html">
  <select v-model="selectedIndex" v-on:change="handleSelect">
    <option v-for="(country, index) in countries" :value="index">{{country.name}}</option>
  </select>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'select-view',
  props: ['countries'],
  data(){
    return {
      selectedIndex: ""
    }
  },
  methods: {
    handleSelect: function() {
      eventBus.$emit('country-selected', this.selectedIndex)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
