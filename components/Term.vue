<template>
  <div>
      <v-card-title>
        1セット目
      </v-card-title>
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
                  v-show="isPlaying"
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
      <v-row
        class="mb-4"
        justify="space-between"
      >
        <v-col cols="4">
          <v-text-field
            v-model="sauna"
            label="サウナ"
            outlined
            class="mt-0 pt-0"
            type="number"
            min="0"
            suffix="分"
          ></v-text-field>
        </v-col>
        <v-col cols="4">
          <v-text-field
            v-model="water"
            label="水風呂"
            outlined
            class="mt-0 pt-0"
            type="number"
            min="0"
            suffix="分"
          ></v-text-field>
        </v-col>
        <v-col cols="4">
          <v-text-field
            v-model="air"
            label="外気浴"
            outlined
            class="mt-0 pt-0"
            type="number"
            min="0"
            suffix="分"
          ></v-text-field>
        </v-col>
      </v-row>


  </div>
</template>

<script>
import Writing from '~/components/Writing.vue'
export default {
  data () {
    return {
      writing: false,
      sauna: { label: 'サウナ',  min: '0', suf: '分'},
      water: { label: '水風呂', min: '0', suf: '分' },
      air: { label: '外気浴', min: '0', suf: '分' },
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
