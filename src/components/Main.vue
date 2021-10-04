<template>
  <div>
      <h1 class="pb-3">Ricerca:</h1>
      <div class="container">
          <div class="row">
              <div class="col-12 pb-3">
                  <h2>Film</h2>
              </div>
              <div v-for="movie in movies" :key="movie.id" class="col-3 p-5">
                    <div>
                      <img :src="img + movie.poster_path" :alt="movie.title">
                    </div>
                    <p> Titolo: {{ movie.title }} </p>
                    <p> Titolo originale: {{ movie.original_title }} </p>
                    <div class="nazionalità">
                        <img v-if="movie.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/64px-Flag_of_Italy.svg.png" alt="bandiera Italia">
                        <img v-else-if="movie.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/64px-Flag_of_the_United_Kingdom_%283-5%29.svg.png" alt="bandiera Inglese" >
                        <p v-else> Lingua: {{ movie.original_language }} </p>
                    </div>
                    <p> Voto {{ movie.vote_average }} </p>

              </div>
          </div>
      </div>
      <div class="container">
          <div class="row">
              <div class="col-12 pb-5">
                  <h2>Serie TV</h2>
              </div>
              <div v-for="serie in tvSerie" :key="serie.id" class="col-3">
                    <p> Titolo: {{ serie.title ? movie.title : serie.name }} </p>
                    <p> Titolo originale: {{ serie.original_title ? serie.original_title : serie.original_name }}  </p>
                    <div class="nazionalità">
                        <img v-if="serie.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/64px-Flag_of_Italy.svg.png" alt="bandiera Italia">
                        <img v-else-if="serie.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/64px-Flag_of_the_United_Kingdom_%283-5%29.svg.png" alt="bandiera Inglese" >
                        <p v-else> Lingua: {{ serie.original_language }} </p>
                    </div>
                    <p> Voto {{ serie.vote_average }} </p>

              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "Main",

    data: function(){
        return{
          img: "https://image.tmdb.org/t/p/w342",
        }
    },
    props: {
        "movies": Array,
        "tvSerie": Array,
    }, 
}

</script>


<style lang="scss">
    img {
      width: 100px;
    }

</style>