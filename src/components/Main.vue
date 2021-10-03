<template>
  <div>
    <div class="input-group mb-3">
      <Header @search="searchFilms"  />
    </div>
    <ul class="d-flex justify-content-space-beetween">
      <li  v-for="(card, index) in filterFilm" :key="index" class="my_card">
        <p> Titolo: {{ card.title }} </p>
        <p> Titolo originale: {{ card.original_title }} </p>
        <p> Lingua: {{ card.original_language }} </p>
        <p> Voto {{ card.vote_average }} </p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Header from './Header.vue'

export default {
  name: 'Main',

  components: {
    Header,
  },

  // props: {
  //   needle: String
  // },

  data(){
    return {
      cards : [],
      films : [],
      needle: "",

    }
  },

  methods:{
    searchFilms : function(needle) {
      this.needle = needle;
    }
  },

  computed:{

    filterFilm : function(){
      let filmTemporaneoList = this.cards.filter(
        (element) => {
          return element.title.toLowerCase().includes(this.needle.toLowerCase())
        }
      );
      return filmTemporaneoList;
    }

  },

  mounted() {
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=8f9f51349841d6d63cd953856f92bc86&query=ritorno+al+futuro&language=it-IT')
    .then((response) => {
      console.log(response.data);
      const result = response.data;
      console.log(result.results);
      const risultato = result.results;
      this.cards = risultato;
    });
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  background-color: aquamarine;
  border: 1px solid blue
}
a {
  color: #42b983;
}
</style>