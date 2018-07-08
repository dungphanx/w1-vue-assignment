<template>
<div id="app">
  <h1>IMDB movies:</h1>
  <div class="nav">
    <button>Lowest rated</button>
    <button>Highest rated</button>
  </div>
  <ul>
    <li
    v-for="(movie, index) in movies.slice(0, 15)"
    :key="index">
      {{ index+1 }}. <span>{{ movie.title }}</span>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  data () {
    return {
      movies: []
    }
  },
  mounted () {
    let self = this
    fetch('https://api.themoviedb.org/3/discover/movie?api_key=d993bdf37f8ab7c574c990434a85a69f&sort_by=popularity.desc').then(function (response) {
      return response.json()
    }).then(function (result) {
      self.movies = result.results
      console.log(result.results)
    })
  }
}
</script>

<style>

</style>
