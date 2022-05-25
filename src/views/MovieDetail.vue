<template>
  <div class="movie-detail" id="movie-detail">
    <h2>{{ movie.Title }}</h2>
    <p><span>Date:</span> {{ movie.Year }}</p>
    <div class="movie-detail-authors">
      <p><span>Director:</span> {{ movie.Director }}</p>
      <p><span>Writer:</span> {{ movie.Writer }}</p>
    </div>
    <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    <p>{{ movie.Plot }}</p>
  </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue'
import { useRoute } from 'vue-router'
import env from '@/env.js'

export default {
  setup() {
    const movie = ref({})
    const route = useRoute()

    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {
          console.log(data)
          movie.value = data
        })
    })

    return {
      movie,
    }
  },
}
</script>
<style lang="scss">
.movie-detail {
  padding: 16px;

  h2 {
    color: #fff;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .featured-img {
    display: block;
    max-width: 100%;
    width: 100%;
    margin-bottom: 16px;
    border-radius: 10px;
  }

  p {
    color: #fff;
    font-size: 14px;
    margin-bottom: 8px;

    span {
      color: #aaa;
    }
  }

  .movie-detail-authors {
    display: flex;

    p + p {
      margin-left: 15px;
    }
  }
}
</style>
