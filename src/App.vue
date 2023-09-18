<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const moviesGenres = ref([])
const TVGenres = ref([])

onMounted(async () => {
  let response = await axios.get('https://api.themoviedb.org/3/genre/movie/list?language=pt-BR', {
    headers: {
      Authorization: `Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIzM2M3OTMzZWZiNjY3MDhiYzRlNDVmZDE1YmNmZjMwZCIsInN1YiI6IjY0ZmYxNTgxMmRmZmQ4MDBhZGI2ZjlhYyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.syZJ3ZTGwMQW9B27IAn7-NpH1peCD1tHJVZKdkrf-e4`
    }
  })
  moviesGenres.value = response.data.genres
  response =  await axios.get('https://api.themoviedb.org/3/genre/tv/list?language=pt-BR', {
    headers: {
      Authorization: `Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIzM2M3OTMzZWZiNjY3MDhiYzRlNDVmZDE1YmNmZjMwZCIsInN1YiI6IjY0ZmYxNTgxMmRmZmQ4MDBhZGI2ZjlhYyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.syZJ3ZTGwMQW9B27IAn7-NpH1peCD1tHJVZKdkrf-e4`
    }
  })
  TVGenres.value = response.data.genres
})
</script>

<template>
  <h1>Gêneros de filmes</h1>
  <ul>
    <li v-for="genre in moviesGenres" :key="genre.id">
      {{ genre.name }}
      {{ genre.id }}
    </li>
  </ul>
  <hr />
  <h1>Gêneros de programas de TV</h1>
  <ul>
    <li v-for="genre in TVGenres" :key="genre.id">
      {{ genre.name }}
      {{ genre.id }}
    </li>
  </ul>
</template>