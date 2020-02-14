<template>
  <q-card class="my-card">
      <q-img src="~assets/starwars.png">
        <div class="absolute-bottom">
          <div class="text-h6">{{ name }}</div>
          <div class="text-subtitle2">{{ gender }}</div>
        </div>
      </q-img>

      <q-card-actions>
        <q-btn
          flat
          dense
          round
          icon="thumb_up_alt"
          title="Curta o personagem"
        ></q-btn>
        <q-btn
          flat
          dense
          round
          icon="thumb_down_alt"
          title="Não Gostei"
        ></q-btn>
      </q-card-actions>
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

    gender: {
      type: String,
      required: true
    }
  }
}
</script>
