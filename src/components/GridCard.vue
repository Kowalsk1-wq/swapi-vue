<template>
  <q-card class="my-card">
      <q-img src="~assets/starwars.png">
        <div class="absolute-bottom">
          <div class="text-h6">{{ name }}</div>
          <div class="text-h6">{{ title }}</div>

          <div class="text-subtitle2">{{ gender === 'male' ? 'Masculino' : gender === 'female' ? 'Feminino' : gender === 'none' ? 'Nenhum' : gender === 'n/a' ? 'Outro' : '' }}</div>
          <div class="text-subtitle2">{{ terrain === 'unknown' ? 'desconhecido' : terrain }}</div>
        </div>
      </q-img>

      <q-card-actions>
        <q-btn
          flat
          dense
          round
          icon="thumb_up_alt"
          title="Curtir"
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
      type: String
    },

    title: {
      type: String
    },

    terrain: {
      type: String
    },

    gender: {
      type: String
    }
  }
}
</script>
