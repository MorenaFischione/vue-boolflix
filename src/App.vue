<template>
  <div id="app">
    <Header @search="cerca" />
    <Main :movies="cards" :tvSerie="tvShows"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from "axios";


export default {
  name: 'App',

  data()  {
    return {
      keyApi : "8f9f51349841d6d63cd953856f92bc86",
      apiFilmsLink : "https://api.themoviedb.org/3/search/movie",
      apiSerieLink : "https://api.themoviedb.org/3/search/tv",
      query : "neddle",
      cards : [],
      tvShows : [],
    }
  },

  components: {
    Header,
    Main
  },

  methods: {
    cerca : function(neddlePassato) {
      axios.get( this.apiFilmsLink, {
        params: {
          api_key : this.keyApi,
          query: neddlePassato,
          language: "it-IT",
        }
      })
      .then((response) => {
      const result = response.data;
      const risultato = result.results;
      this.cards = [...risultato];
      });

      axios.get( this.apiSerieLink, {
        params: {
          api_key : this.keyApi,
          query: neddlePassato,
          language: "it-IT",
        }
      })
      .then((response) => {
      const result = response.data;
      const risultato = result.results;
      this.tvShows = [...risultato];
      });
    }
  },
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
  
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
