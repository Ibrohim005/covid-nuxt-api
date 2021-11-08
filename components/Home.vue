<template>
  <div class="container mx-auto px-4 text-center">
        <div class="flex items-center justify-center mx-auto">
            <h1 class="text-6xl">
                Covid-19 Cases In {{ searchResults.country }}
            </h1>
            <img :src="searchResults.countryInfo.flag" alt="Country flag" class="w-20 h-10 ml-3">
        </div>
        <input class="border p-3 rounded-md mt-4 text-xl" placeholder="Enter country ==>" type="text" v-model="query" @keypress.enter="search">
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-2 mt-4">
            <div class="card bg-blue-400 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Active Cases
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.active}}
                </p>
            </div>
            <div class="card bg-purple-400 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Total Cases
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.cases}}
                </p>
            </div>
            <div class="card bg-blue-400 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Critical Cases
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.critical}}
                </p>
            </div>
            <div class="card bg-red-400 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Total Death
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.deaths}}
                </p>
            </div>
            <div class="card bg-green-400 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Recovered Cases
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.recovered}}
                </p>
            </div>
            <div class="card bg-gray-400 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Total Test Done
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.tests}}
                </p>
            </div>
            <div class="card bg-red-600 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Today deathes
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.todayDeaths}}
                </p>
            </div>
            <div class="card bg-green-600 text-white p-4 rounded-lg">
                <h2 class="card__title text-4xl">
                    Today recovered
                </h2>
                <p class="card__res p-1 rounded-md mt-2 border-2 border-white inline-block text-3xl">
                    {{searchResults.todayRecovered}}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            query: '',
            url_base: 'https://corona.lmao.ninja/v2/countries/',
            searchResults: {
                country: '',
                active: '00000',
                cases: '00000',
                critical:'00000',
                deaths: '00000',
                recovered: '00000',
                tests: '00000',
                todayDeaths: '00000',
                todayRecovered: '00000',
                countryInfo: {
                    flag: ''
                }
            }
        };
    },
    methods: {
    search() {
      axios
        .get(`${this.url_base}${this.query}`)
        .then((response) => {
          this.searchResults = response.data;
          console.log(this.searchResults);
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dongle:wght@300;400;700&display=swap');
body{
    font-family: Dongle;
    background-color: #663dff;
    background-image: linear-gradient(319deg, #663dff 0%, #aa00ff 37%, #cc4499 100%);
    background-repeat: no-repeat;
}
</style>