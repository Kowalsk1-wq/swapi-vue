<template>
  <q-page class="cards">
    <GridCard
      class="cardMov"
      v-for="mov in movies"
      :key="mov.title"
      v-bind="mov"
    />
  </q-page>
</template>

<style scoped>
  .cards {
    display: inline-block;
    width: 100%;
    padding:10px;
    padding-left: 14.50%;
    vertical-align: center;
    justify-content: center;
  }

  .cardMov {
    width: 25%;
    float:left;
    display:block;
    margin: 10px 10px 10px 20px;
  }
</style>

<script>
import GridCard from 'components/GridCard'

import axios from 'axios'

export default {
  name: 'pageMovies',

  components: {
    GridCard
  },

  data () {
    return {
      movies: null
    }
  },

  mounted () {
    axios
      .get('https://swapi.co/api/films/')
      .then(res => (this.movies = res.data.results))
  }
}
</script>
