<template>
  <q-page class="flex flex-center cards">
    <GridCard
      v-for="char in chars"
      :key="char.name"
      v-bind="char"
    />
  </q-page>
</template>

<style scoped>
  .cards {
    flex-direction: column;
  }

  .cardChar {
    width: 350px;
    height: auto;
    margin-top: 15px;
    margin-bottom: 10px;
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
