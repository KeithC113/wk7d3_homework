<template lang="html">
  <div>
    <h1>List of all the world's countries</h1>

    <!-- <div class="main-container">
      <countries-list :countries='countries'></countries-list>
      <country-detail :country='selectedCountry'></country-detail>
    </div> -->

    <div class="drop-down">
      <country-select :countries="countries"></country-select>
    </div>
    <div class="main-container">
      <country-detail :country ='selectedCountry'></country-detail>
    </div>
  </div>

</template>

<script>
import {eventBus} from './main.js';
// import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import CountrySelector from './components/CountrySelector.vue';

export default {
  name: 'app',
  data(){
    return {
      countries:[],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries =>this.countries = countries)

    eventBus.$on('country-selected', (country)=>{
      this.selectedCountry = country
    })
  },
  components: {
    // "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "country-select": CountrySelector
  }
}
</script>

<style>
.main-container {
    display: flex;
    justify-content: space-between;
  }
.med-flag {
    height: 30px
  }
</style>
