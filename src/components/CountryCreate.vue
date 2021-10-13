<template>
  <div>
    <div v-for="country in countriesList" :key="country.id">
      <img :src="country.flag" alt="">
      <h1>{{ country.name }}</h1>
      <p >{{country.name}}</p>
      
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
          .get('https://restcountries.com/v2/all')  // Does a get request
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

</style>