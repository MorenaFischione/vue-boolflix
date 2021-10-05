<template>
  <div class="my_box p-5">
      <div class="container">
          <div class="row justify-content-evenly">
            <div class="col-12">
              <h1 class="p-5 my_title">Films:</h1>
            </div>
            <div v-for="movie in movies" :key="movie.id" class="col-3 p-2 me-3 mb-5 my_card">
                  <div class="my_contain">
                    <img :src="immagine(img , movie.poster_path)" :alt="movie.title">
                    <p class="h6"> <strong>Titolo:</strong> {{ movie.title }} </p>
                    <p class="h6">  <strong>Titolo originale:</strong> {{ movie.original_title }} </p>
                    <div class="my_voto">
                      <span> <strong> Voto:</strong> </span>
                      <i class="fas fa-star" 
                      v-for=" n in arrotondarmento(movie.vote_average)" :key="'star'+n" > </i>
                      <i class="far fa-star" 
                      v-for=" n in 5 - arrotondarmento(movie.vote_average)" :key="'emptystar'+n" > </i>
                    </div>
                    <div class="my_overwiew">
                      <p> <strong>Overwiew:</strong> {{ movie.overview }}</p>
                  </div>      
            </div>
        </div>
      </div>
      <div class="container">
          <div class="row justify-content-evenly">
            <div class="col-12">
              <h1 class="p-5 my_title">Serie tv</h1>
            </div>
            <div v-for="serie in tvSerie" :key="serie.id" class="col-3 p-2 me-3 mb-5 my_card">
                  <div class="my_contain">
                    <img :src="immagine(img , serie.poster_path)" :alt="serie.title">
                    <p class="h6"> Titolo: {{ serie.title ? serie.title : serie.name }} </p>
                    <p class="h6"> Titolo originale: {{ serie.original_title ? serie.original_title : serie.original_name }}  </p>
                    <div class="my_voto">
                      <span> <strong> Voto:</strong> </span>
                      <i class="fas fa-star" 
                      v-for=" n in arrotondarmento(serie.vote_average)" :key="'star'+n" > </i>
                      <i class="far fa-star" 
                      v-for=" n in 5 - arrotondarmento(serie.vote_average)" :key="'emptystar'+n" > </i>
                    </div>
                    <div class="my_overwiew">
                      <p> <strong>Overwiew:</strong> {{ serie.overview }}</p>
                  </div>    
                  </div>
            </div>
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
          imgGenerica: "",
        }
    },
    props: {
        "movies": Array,
        "tvSerie": Array,
    }, 

    methods: {
        arrotondarmento : function(valore){
            let valoreModificato = valore / 2;
            let arrotondato = Math.ceil(valoreModificato);
            console.log(arrotondato);
            return arrotondato;
        },

        immagine : (img, valore) => {
          let imgUrl = img + valore;
          if (valore == null) {
            console.log(valore);
            imgUrl = "https://via.placeholder.com/342x513";
            console.log(imgUrl);
            return imgUrl;
          } else {
            return imgUrl;
          }
        }
        
    },

}

</script>


<style lang="scss">
    @import "~@fortawesome/fontawesome-free/css/all.css";


    .my_box {
      background-color: #3c3838;

      .my_title {
       color: white;
      }
    }


    .my_card {
      height: 513px;
      width: 400px;
      border:1px solid white;

      img {
        object-fit: cover;
        width: 100%;
      }

      p,
      span,
      i {
        color: white;
        display: none;
      }
      
      .my_overwiew {
      min-height: 250px;
      max-height: 310px;
      overflow: hidden;
      display: none;
      }


      .my_contain:hover {

        .my_card{
          
        }

        img {
          display: none;
        }

        p,
        span,
        i {
          color: white;
          display: inline-block;
        }
      
        .my_overwiew {
        min-height: 250px;
        max-height: 310px;
        overflow: hidden;
        display: block;
        }
      }
      
    }

    


</style>