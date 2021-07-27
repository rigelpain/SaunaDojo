<template>
  <div class="ma-5">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        class="ma-2 px-5"
        rounded
        large
        dark
        color="indigo"
        v-bind="attrs"
        v-on="on"
      >
        <v-icon small class="mr-2">far fa-edit</v-icon>
        サ活記録
      </v-btn>
    </template>
      <v-card>
        <v-toolbar
          color="primary"
        >
          <v-btn
            icon
            dark
            @click="dialog = false"
          >
            <v-icon>mdi-close</v-icon>
          </v-btn>
          <v-toolbar-title>新しいサ活記録</v-toolbar-title>
          <v-toolbar-items>
            <v-btn
              dark
              text
              right
              @click="dialog = false"
            >
              完了
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
        <Writing />
      </v-card>
    </v-dialog>


    <v-row no-gutters>
      <v-col cols="12">
        <p class="text-h4">最新のサ活</p>
        <Card1 />
      </v-col>
    </v-row>
    <v-card>
      <v-card-title>過去のベストサ活</v-card-title>
    </v-card>

  </div>
</template>

<script>
import Writing from '~/components/Writing.vue'
import Card1 from '~/components/Card1.vue'

export default {
  data () {
      return {
        writing: false,
        dialog: false,
        bpm: 40,
        interval: null,
        isPlaying: true,

      }
    },
  computed: {
    color () {
      if (this.bpm < 20) return 'indigo'
      if (this.bpm < 40) return 'teal'
      if (this.bpm < 60) return 'green'
      if (this.bpm < 80) return 'orange'
      return 'red'
    },
    heartBeat () {
      return `${ 30 / (this.bpm+30) }s`
    },
    heartBeat_01_02 () {
      return `${ 30 / 110 }s`
    },
  },
  components: {
    Writing,
    Card1,
  }
}

</script>

<style>

@keyframes heartBeatAnimation {
  from {
    transform: scale(.5);
  }

  to {
    transform: scale(1);
  }
}

</style>



