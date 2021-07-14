<template>
  <div class="mt-5">

      <v-toolbar
        flat
        dense
      >
        <v-toolbar-title>
          <span class="subheading">評価</span>
        </v-toolbar-title>
      </v-toolbar>

      <v-card-text>
        <v-row
          class="mb-4"
          justify="space-between"
        >
          <v-col class="text-right">
            <span
              class="text-h2 font-weight-light"
              v-text="bpm"
            ></span>
            <span class="subheading font-weight-light mr-1">pt</span>
            <v-fade-transition>
              <v-avatar
                v-if="isPlaying"
                :color="color"
                :style="{
                  animationDuration: heartBeat
                }"
                class="mb-1 v-avatar--metronome"
                size="12"
              ></v-avatar>
            </v-fade-transition>
          </v-col>
        </v-row>

        <v-slider
          v-model="bpm"
          :color="color"
          track-color="grey"
          always-dirty
          min="0"
          max="100"
        >
          <template v-slot:prepend>
            <v-icon
              :color="color"
              @click="decrement"
            >
              mdi-minus
            </v-icon>
          </template>

          <template v-slot:append>
            <v-icon
              :color="color"
              @click="increment"
            >
              mdi-plus
            </v-icon>
          </template>
        </v-slider>
      </v-card-text>


  </div>
</template>

<script>
import Writing from '~/components/Writing.vue'
export default {
  data () {
    return {
      writing: false,
      slider: { label: 'thumb-color', val: 50, color: 'red', min: '0', max: '100' },
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
      return `${ 30 / (this.bpm+1) }s`
    },
  },

  methods: {
    decrement () {
      this.bpm--
    },
    increment () {
      this.bpm++
    },
    toggle () {
      this.isPlaying = !this.isPlaying
    },
  },
  components: {
    Writing,
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

.v-avatar--metronome {
  animation-name: heartBeatAnimation;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}

</style>
