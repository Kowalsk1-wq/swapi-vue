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
    axios
      .get('https://swapi.co/api/people/')
      .then(res => (this.chars = res.data.results))
  }
}
</script>
