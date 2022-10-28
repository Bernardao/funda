<!-- <script lang="ts" setup> -->
<script setup>
// definePegaMeta({
//   title: 'MovieSearch',
//   // pageTransitions: false,
// })
const query = ref('batman')
const movies = ref([])
const URL = 'https://www.omdbapi.com/?'
const API_KEY = 'apikey=fcfa379e'
// const api_query = 'i=tt3896198'
async function searchQuery() {
  const busqueda = await $fetch(`${URL}${API_KEY}&s=${query.value}`)
  movies.value = busqueda.Search
}
searchQuery()
</script>

<template>
  <div class="movies-index">
    <form @submit.prevent="searchQuery()">
      <input type="text" v-model="query" />
      <button>Search</button>
    </form>
    <ul class="movie-list">
      <li v-for="movie in movies" :key="movie.imdbID">
        <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
          <img :src="movie.Poster" :alt="movie.title" />
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.movie-list {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
