<template>
  <div class="app font-monospace">
    <div class="content">
      <app-info 
        v-bind:allMoviesCount="movies.length" 
        v-bind:favouriteMoviesCount="movies.filter(m => m.favourite).length"  
      />
      <div class="search-panel">
        <search-panel v-bind:updateTermHandler="updateTermHandler"/>
        <app-filter v-bind:updateFilterHandler="updateFilterHandler"/>
      </div>
      <movie-list 
        v-bind:movies="onFilterHandler(onSearchHandler(movies, term), filter)"
        v-on:onToggle="onToggleHandler"
        v-on:onDelete="onDeleteHandler"
      />
      <movie-add-form @createMovie="createMovie"/>
    </div>
  </div>
</template>

<script>
  import AppInfo from '@/components/app-info/AppInfo.vue';
  import SearchPanel from '@/components/search-panel/SearchPanel.vue';
  import AppFilter from '@/components/app-filter/AppFilter.vue';
  import MovieList from '@/components/movie-list/MovieList.vue';
  import MovieAddForm from '@/components/movie-add-form/MovieAddForm.vue';

  export default {
    components: {
      AppInfo,
      SearchPanel,
      AppFilter,
      MovieList,
      MovieAddForm,
    },
    data() {
      return {
        movies: [
            {
              id: 1,
              name: "Omar",
              viewers: 811,
              favourite: false,
              like: true
            },
            {
              id: 2,
              name: "Empire of Osman",
              viewers: 756,
              favourite: true,
              like: false
            },
            {
              id: 3,
              name: "Ertugrul",
              viewers: 440,
              favourite: true,
              like:true
            }
        ],
        term: "",
        filter: "all"
      }
    },
    methods: {
      createMovie(item) {
        this.movies.push(item)
      },

      onToggleHandler({id, prop}) {
        this.movies = this.movies.map(item => {
          if (item.id == id) {
            return {...item, [prop]: !item[prop]}
          }
          return item
        })
      },

      onDeleteHandler(id) {
        console.log(id);
        this.movies = this.movies.filter(c => c.id !== id)
      },

      onSearchHandler(arr, term) {
        if (term.length == 0) {
          return arr
        }
        return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
      },

      onFilterHandler(arr, filter) {
        switch (filter) {
          case "popular":
            return arr.filter(c => c.like)
            break;
          case "mostViewers":
            return arr.filter(c => c.viewers >= 500)
            break;
          default:
            return arr;
            break;
        }
      },
       
      updateFilterHandler(filter) {
        this.filter = filter
      },

      updateTermHandler(term) {
        this.term = term
      }
    }
  }
</script>

<style scoped>
.app {
  height: 100vh;
  color: #000;
}
.content {
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}
.search-panel {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(3, 82, 62, 0.215);
}
</style>