<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="all">
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title class="title">
          Star Wars Universe
        </q-toolbar-title>

        <div>v{{ version }}</div>

        <q-btn
          style="margin-left: 10px;"
          flat
          dense
          round
          @click=redirect
          icon="home"
          v-if="this.isHome() === false"
        />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label header class="text-grey-8">Links</q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink'

export default {
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  data () {
    return {
      id: EssentialLink.id,
      leftDrawerOpen: false,
      version: '1.0.0',
      redirect: async () => {
        this.$router.push('/')
      },
      isHome: () => {
        if (window.location.href === 'http://localhost:8080/#/') return true
        else return false
      },
      essentialLinks: [
        {
          id: '1',
          title: 'Characters',
          caption: 'Veja todos os Personagens',
          icon: 'face',
          link: '/#/chars'
        },
        {
          id: '2',
          title: 'Movies',
          caption: 'Conheça todos os filmes!',
          icon: 'movie',
          link: '/#/movies'
        },
        {
          id: '3',
          title: 'Planets',
          caption: 'Planetas do universo Star Wars',
          icon: 'language',
          link: '/#/planets'
        }
      ]
    }
  }
}
</script>

<style scoped>
  * {
    font-family: Georgia, 'Times New Roman', Times, serif, sans-serif
  }

  .title {
    font-size: 20pt;
    font-weight: bold;
    align-self: center;
  }

  .all {
    background-color: #000!important;
  }
</style>
