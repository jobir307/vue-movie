<template>
  <div class="movie-add-form">
    <h3>Yangi kino qo'shish</h3>
    <form class="add-form d-flex">
      <input 
        type="text" 
        class="form-control new-movie-label" 
        placeholder="Qanday kino?" 
        v-bind:value="movie.name"
        v-on:input="movie.name = $event.target.value"
      />
      <input 
        type="number" 
        class="form-control new-movie-label" 
        placeholder="Necha marotaba ko'rilgan?" 
        v-bind:value="movie.viewers"
        v-on:input="movie.viewers = $event.target.value"
      />
      <button class="btn btn-outline-dark" type="submit" v-on:click="addMovie">Qo'shish</button>
    </form>
    </div>
</template>

<script>
    export default {
      name: 'movie-add-form',
      data() {
        return {
            movie: {
              name: "",
              viewers: ""
            }
        }
      },
      methods: {
        addMovie(e) {
          e.preventDefault()
          if (!this.movie.name || !this.movie.viewers) return
          let newMovie = {
            id: Date.now(),
            name: this.movie.name,
            viewers: this.movie.viewers,
            favourite: false,
            like: false
          }
          this.$emit('createMovie', newMovie)
          this.movie = {}
        } 
      }
    }
</script>

<style scoped>
.movie-add-form {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(3, 82, 62, 0.215);
}
</style>