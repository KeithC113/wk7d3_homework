<template lang="html">
  <div v-if='country'>
    <h3>{{country.name}}</h3>
    <img class="med-flg" :src="country.flag"/>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p>Region: {{country.region}}</p>
    <p>Languages: </p>
    <ul>
      <li v-for"langauge in country.languages">{{langauge.name}}</li>
    </ul>
   <ul>
     <li v-for="border in country.borders">{{border}}</li>
   </ul>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props:['country']
}
</script>

<style lang="css" scoped>

</style>
