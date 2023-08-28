<template>
    <div class="btn-group">
        <button 
          class="btn"
          :class="this.filter == 'all' ? 'btn-dark' : 'btn-outline-dark'" 
          type="button"
          v-on:click="filterHandler('all')"
        >
          Barcha kinolar
        </button>
        <button 
          class="btn" 
          :class="this.filter == 'popular' ? 'btn-dark' : 'btn-outline-dark'" 
          type="button"
          v-on:click="filterHandler('popular')"
        >
          Mashhur kinolar
        </button>
        <button 
          class="btn"
          :class="this.filter == 'mostViewers' ? 'btn-dark' : 'btn-outline-dark'"  
          type="button"
          v-on:click="filterHandler('mostViewers')"
        >
          Eng ko'p ko'rilgan kinolar
        </button>
    </div>
</template>

<script>
    export default {
      name: 'app-filter',
      props: {
        updateFilterHandler: {
          type: Function,          
          required: true,
        }
      },
      data() {
        return {
          filter: "all"
        }
      },
      methods: {
        filterHandler(filter) {
          this.filter = filter
          this.updateFilterHandler(this.filter)
        }
      }
    }
</script>

<style scoped>

</style>