
<template>
    <div id="movie-list"> 
      <div v-for="movie in filteredMovies" class="movie" :key="movie.title"> {{movie.title}} </div>
    </div>
</template>

<script>
  import genres from '../util/genres.js';
  export default {
    data: function(){
      return {
        movies: [
          {'title': 'Pulp fiction', 'genre': genres.CRIME},
          {'title': 'Jurassic park', 'genre': genres.COMEDY},
          {'title': 'Avatar', 'genre': genres.COMEDY},
        ]
      }
    },
    props: ['genre', 'time'],
    methods:{
      moviePassesGenreFilter(movie){
        if(!this.genre.length){
          return true;
        }else{
          return this.genre.find(genre => movie.genre===genre);
        }
        
      }
    },
    computed: {
      filteredMovies(){
        return this.movies.filter(this.moviePassesGenreFilter);
      }
    }
  }
</script>