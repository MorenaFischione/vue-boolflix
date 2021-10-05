<template>
  <div class="mb-3 pe-5 ps-5 my_container">
      <div>
          <img src="https://toppng.com/uploads/preview/netflix-logo-vector-free-download-11574237114rh16slxpn2.png" alt="">
      </div>
      <div class="my_ricerca">
        <input v-model.trim="needle" type="text" class="form-control" placeholder="Cerca un film" @keyup= "$emit('search', needle)">
        <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click= "$emit('search', needle)" >Cerca</button>
      </div>
  </div>
</template>

<script>
export default {
    name: "Header",

    data() {
        return {
            needle: "",
        }
    }, 

}
</script>

<style lang="scss" scoped>

.my_container {
    display: flex;
    justify-content: space-between;
    background-color: black;

    .my_ricerca {
        display: flex;
        align-items: center;
    }
}

</style>