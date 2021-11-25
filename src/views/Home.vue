<template>
  <div>
    <div v-if="!loading">
      <p>
        <data-title :text="title" :dateData="datedata"></data-title>
        <data-boxes :stats="stats"></data-boxes>
        <data-country :countries="countries" @get-country='getCountryData'></data-country>
        <button v-if='stats.Country' @click="clearCountry">Clear Country</button>
      </p>
    </div>
    <div v-else>{{ loadingStatus }}</div>
  </div>
</template>

<script>

import DataBoxes from '../components/DataBoxes.vue'
import DataCountry from '../components/DataCountry.vue'
import DataTitle from '../components/DataTitle.vue'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    DataCountry
  },
  data(){
    return{
      loading: true,
      title: 'Global',
      datedata: '',
      stats: {},
      countries: [],
      loadingStatus: 'Loading...'
    }
  },
  methods:{
    async fetchcovidData(){
      const res = await  fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
    async clearCountry(){
      this.loading = true
      const data = await this.fetchcovidData()
      this.title = 'Global'
      this.stats = data.Global
      this.loading = false
    }
  },
  async created(){
    const data = await this.fetchcovidData()
    this.datedata = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  }
}
</script>

<style scoped>
button{
  background-color: grey;
  color: white;
  border: 2px solid black;
  margin-top: 5%
}
</style>


