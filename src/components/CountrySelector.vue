<template lang="html">
  <div>
    <select v-model="selectedCountry" v-on:change"handleChange">
      <option v-for="(country, index) in countries" :country="country" :key="index">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'country-select'
  props: ['countries'],
  methods:{
    handleClick(){
      eventBus.$emit('country-selected',this.selectedCountry)
    }
  },
  data(){
    return {
      selectedChange: null 
    }
  }
}
</script>

<style lang="css" scoped>
</style>
