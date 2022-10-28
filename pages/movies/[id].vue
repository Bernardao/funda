<script setup>
const route = useRoute()
const URL = 'https://www.omdbapi.com/?'
const API_KEY = 'apikey=fcfa379e'
const routeId = route.params.id
const { data } = await useFetch(`${URL}${API_KEY}&i=${routeId}`, {
  pick: ['Title', 'Year', 'Plot', 'Poster'],
  key: `/movies/${routeId}`,
  onResponse({ request, response }) {
    if (response._data.Error === 'Incorrect IMDb ID.') {
      // console.log('Inside error', response._data.Error)
      // throw createError({ statusCode: 404, statusMessage: 'Page Not Found' })
      // showError('😱 Oh no, an error has been thrown.')
      showError({ statusCode: 404, statusMessage: 'Página no encontrada' })
    }
  },
})
useHead({
  title: data.value.Title,
  meta: [
    { name: 'description', content: data.value.Plot },
    { property: 'og:description', content: data.value.Plot },
    { property: 'og:image', content: data.value.Poster },
    { name: 'twitter:card', content: `summary_large_image` },
  ],
})
</script>
<template>
  <div>
    <h1>
      <pre>
        {{ data }}
      </pre>
    </h1>
  </div>
</template>

<style scoped></style>
