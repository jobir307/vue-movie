<template>
    <ul class="movie-list list-group">
        <movie-list-item 
            v-for="movie in movies" 
            :key="movie.id" 
            v-bind:movie="movie"
            @onToggle="$emit('onToggle', $event)"
            @onDelete="$emit('onDelete', movie.id)"
        />
    </ul>
</template>

<script>
import MovieListItem from '@/components/movie-list-item/MovieListItem.vue'
    export default {
        name: 'movie-list',
        components: { 
            MovieListItem
        },
        props: {
            movies: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
.movie-list {
    margin-bottom: 1rem;
    padding: 1.2rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(3, 82, 62, 0.215);
}
</style>