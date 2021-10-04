<template>
  <div class="input-group mb-3">
      <input v-model.trim="needle" type="text" class="form-control" placeholder="Cerca un film" @keyup= "$emit('search', needle)">
      <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click= "$emit('search', needle)" >Cerca</button>
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

<style>

</style>