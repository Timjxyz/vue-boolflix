<template>
  <div id="app">
    <MyHeader @search="doSearch" />
    <MyMain :films="films" :series="series"/>

  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'
const axios = require('axios');

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data(){
    return{
      films:[],
      series:[],
      apy_key:'d7660e56e06ac105e09f6f82264e7f01',
      language:'it-IT'
    }
  },
  methods:{
    doSearch(keyword){
      const params={
          params:{
            'api_key':this.apy_key,
            'query':keyword,
            'language':this.language
          }
        };
        this.getFilms(params);
        this.getTv(params);

    },

    getFilms(params) {

        axios.get('https://api.themoviedb.org/3/search/movie/' , params)
        
        .then((response) => {
            this.films = response.data.results;
    
          })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
        

    },
    getTv(params) {
        axios.get('https://api.themoviedb.org/3/search/tv/' , params)
        
        .then((response) => {
            this.series = response.data.results;
    
          })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
        

    },
  }
}
</script>

<style lang="scss">

  *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
  }
</style>
