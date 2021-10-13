<template>
  <div>
    <div class="container main-container">
      <div class="country-box" v-for="country in countriesList.slice(0, 12)" :key="country.id">
      <img :src="country.flag" alt="countries-flag" width="264" height="160">
      <h3>{{ country.name }}</h3>
      <p class="main-item-text">Population: {{ country.population }}</p>
      <p class="main-item-text">Region: {{ country.region }}</p>
      <p class="main-item-text">Capital: {{ country.capital }}</p> 
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

  export default {
    data(){
      return{
        countriesList: []
      }
    },
    // methods: {
    //   getCountries() {
    //     const country = "https://restcountries.com/v2/all";

    //     fetch(country)
    //       .then(res => res.json())
    //       .then(data => {
    //         return this.countriesList = [...data.slice(0,8)]
    //       })
    //     console.log(this.countriesList[0]);
    //   }
    // },
    created() {
        axios
          .get('https://restcountries.com/v2/all?limit=8')  // Does a get request
          .then(response => {
            this.countriesList = response.data
            console.log(response.data);
          })
          .catch(error => {
            console.log('There was an error:', error.response) // Logs out the error
          })
    }
  }
</script>

<style scoped>
.main-container{
  padding: 0;
  padding-top: 48px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.country-box{
  margin-top: 75px;
  box-shadow: 0px 0px 7px 2px rgba(0, 0, 0, 0.0294384);
  border-radius: 5px;
}

</style>