<template>
  <q-page class="cards">
    <GridCard
      class="cardChar"
      v-for="char in chars"
      :key="char.name"
      v-bind="char"
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
  name: 'pageCharacters',

  components: {
    GridCard
  },

  data () {
    return {
      chars: null
    }
  },

  mounted () {
    axios.all([
      axios.get('https://swapi.co/api/people/?page=1'),
      axios.get('https://swapi.co/api/people/?page=2'),
      axios.get('https://swapi.co/api/people/?page=3'),
      axios.get('https://swapi.co/api/people/?page=4'),
      axios.get('https://swapi.co/api/people/?page=5'),
      axios.get('https://swapi.co/api/people/?page=6'),
      axios.get('https://swapi.co/api/people/?page=7'),
      axios.get('https://swapi.co/api/people/?page=8'),
      axios.get('https://swapi.co/api/people/?page=9')
    ]).then(axios.spread((pg1, pg2, pg3, pg4, pg5, pg6, pg7, pg8, pg9) => {
      this.page1 = pg1.data.results
      this.page2 = pg2.data.results
      this.page3 = pg3.data.results
      this.page4 = pg4.data.results
      this.page5 = pg5.data.results
      this.page6 = pg6.data.results
      this.page7 = pg7.data.results
      this.page8 = pg8.data.results
      this.page9 = pg9.data.results

      this.chars = [
        ...this.page1,
        ...this.page2,
        ...this.page3,
        ...this.page4,
        ...this.page5,
        ...this.page6,
        ...this.page7,
        ...this.page8,
        ...this.page9
      ]
    }))
  }
}
</script>
<!-- res => (this.chars = res.data.results) -->
