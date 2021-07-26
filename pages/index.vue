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
    </v-toolbar>

    
    
    
  </v-card>



  
</template>

<script>
  import Sakatsu from '~/components/Sakatsu.vue'
  import Shisho from '~/components/Shisho.vue'

  export default {
    data () {
      return {
        tab: null,
      }
    },
    components: {
      Sakatsu,
      Shisho
    },
  }
</script>

<style module>
</style>