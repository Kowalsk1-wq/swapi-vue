<template>
  <q-page class="cards">
    <GridCard
      class="cardChar"
      v-for="pln in planets"
      :key="pln.name"
      v-bind="pln"
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

  .cardChar {
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
  name: 'pagePlanets',

  components: {
    GridCard
  },

  data () {
    return {
      planets: null
    }
  },

  mounted () {
    axios.all([
      axios.get('https://swapi.co/api/planets/?page=1'),
      axios.get('https://swapi.co/api/planets/?page=2'),
      axios.get('https://swapi.co/api/planets/?page=3'),
      axios.get('https://swapi.co/api/planets/?page=4'),
      axios.get('https://swapi.co/api/planets/?page=5'),
      axios.get('https://swapi.co/api/planets/?page=6'),
      axios.get('https://swapi.co/api/planets/?page=7')
    ]).then(axios.spread((pg1, pg2, pg3, pg4, pg5, pg6, pg7) => {
      this.page1 = pg1.data.results
      this.page2 = pg2.data.results
      this.page3 = pg3.data.results
      this.page4 = pg4.data.results
      this.page5 = pg5.data.results
      this.page6 = pg6.data.results
      this.page7 = pg7.data.results

      this.planets = [
        ...this.page1,
        ...this.page2,
        ...this.page3,
        ...this.page4,
        ...this.page5,
        ...this.page6,
        ...this.page7
      ]
    }))
  }
}
</script>
