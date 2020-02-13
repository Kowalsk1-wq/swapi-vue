<template>
  <q-card class="cardChar">
      <q-card-section>
        <div class="text-h4">{{ name }}</div>
      </q-card-section>
      <q-card-section>
        <div class="text-h6">{{ birth_year }}</div>
      </q-card-section>
    </q-card>
</template>

<script>
export default {
  name: 'GridCard',
  props: {
    name: {
      type: String,
      required: true
    },

    birth_year: {
      type: String,
      required: true
    }
  }
}
</script>
