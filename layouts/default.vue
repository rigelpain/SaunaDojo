<template>
  <v-app dark>
    <v-app-bar collapse-on-scroll app>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-app-bar-title>サウナ道場</v-app-bar-title>
    </v-app-bar>
    <v-main>
      <Nuxt />
      <v-tabs-items v-model="tab">
      <v-tab-item>
        <Sakatsu />
      </v-tab-item>
      <v-tab-item>
        <Shisho />
      </v-tab-item>
    </v-tabs-items>
    </v-main>
    <v-footer
      fixed
      app
    >
      <v-tabs
        v-model="tab"
        fixed-tabs
        icons-and-text
      >
        <v-tabs-slider></v-tabs-slider>
        <v-tab>
          サ活記録
          <v-icon>fas fa-clipboard-list</v-icon>
        </v-tab>
        <v-tab>
          シショー
          <v-icon>mdi-heart</v-icon>
        </v-tab>
      </v-tabs>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
      tab: null,
    }
  }
}
</script>

<style scoped>
</style>
