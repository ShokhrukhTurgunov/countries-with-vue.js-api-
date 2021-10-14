<template>
  <div>
    <div class="container main-container">
      <div class="country-box" v-for="country in countriesList.slice(0, 12)" :key="country.id">
      <img class="country-flag" :src="country.flag" alt="countries-flag" width="264" height="160">
      <h3 class="country-name">{{ country.name }}</h3>
      <p class="country-text">Population: <span>{{ country.population }}</span></p>
      <p class="country-text">Region: <span>{{ country.region }}</span></p>
      <p class="country-text">Capital: <span>{{ country.capital }}</span></p> 
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
   width: 264px;
    padding: 0;
    padding-bottom: 40px;
    margin-bottom: 75px;
    display: flex;
    flex-direction: column;
    background: #FFFFFF;
    box-shadow: 0px 0px 7px 2px rgba(0, 0, 0, 0.0294384);
    border-radius: 5px;
    color: #2B3844;
    transition: .5s ease;
}

.country-box:hover{
  box-shadow: 0px 3px 2px #2222228f;
}

.country-flag{
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.country-name{
    margin: 24px 0 16px 24px;
    font-weight: 800;
    font-size: 18px;
    line-height: 26px;
}

.country-text{
    margin: 0;
    margin-bottom: 8px;
    margin-left: 24px;
    font-weight: 600;
    font-size: 14px;
    line-height: 16px;
}

.country-text span{
  font-weight: 300;
  font-size: 14px;
  line-height: 16px;
}

</style>