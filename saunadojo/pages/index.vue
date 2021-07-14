<template>
  <v-card>
    <v-toolbar
      color="orange darken-1"
      dark
      flat
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>サウナ道場</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs
          v-model="tab"
          align-with-title
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>
          <v-tab>
            サ活記録
          </v-tab>
          <v-tab>
            シショー
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="tab">
      <v-tab-item>
        <Sakatsu />
      </v-tab-item>
      <v-tab-item>
        <Shisho />
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
  import Sakatsu from '~/components/Sakatsu.vue'
  import Shisho from '~/components/Shisho.vue'

  export default {
    data () {
      return {
        tab: null,
        tabItems: [
          'サ活記録', 'シショー',
        ],
        text: 'Lorem ipsum dolor sit amet, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      }
    },
    components: {
      Sakatsu,
      Shisho
    },
  }
</script>
