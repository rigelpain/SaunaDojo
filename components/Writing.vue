<template>
  <div>
    <v-card-title>
      <span class="text-h5">新しいサ活記録</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col
            cols="12"
          >
            <Term />
          </v-col>

          <v-col
            v-if="step>=2"
            cols="12"
          >
            <Term2 />
          </v-col>

          <v-col
            v-if="step>=3"
            cols="12"
          >
            <Term3 />
          </v-col>

          <v-col class="d-flex justify-center">
            <v-btn
              class="mx-auto"
              fab
              dark
              color="indigo"
              @click="setIncrement"
            >
              <v-icon dark>
                mdi-plus
              </v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-card-text>
    <v-toolbar
      flat
      color="transparent"
    >
      <v-toolbar-title>施設情報</v-toolbar-title>
    </v-toolbar>

    <v-container class="py-0">
      <v-row
        align="center"
        justify="start"
      >
        <v-col
          v-for="(selection, i) in selections"
          :key="selection.text"
          class="shrink"
        >
          <v-chip
            :disabled="loading"
            close
            @click:close="selected.splice(i, 1)"
          >
            <v-icon
              left
              v-text="selection.icon"
            ></v-icon>
            {{ selection.text }}
          </v-chip>
        </v-col>

        <v-col
          v-if="!allSelected"
          cols="12"
        >
          <v-text-field
            ref="search"
            v-model="search"
            full-width
            hide-details
            label="Search"
            single-line
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>

    <v-divider v-if="!allSelected"></v-divider>

    <v-list>
      <template v-for="item in categories">
        <v-list-item
          v-if="!selected.includes(item)"
          :key="item.text"
          :disabled="loading"
          @click="selected.push(item)"
        >
          <v-list-item-avatar>
            <v-icon
              :disabled="loading"
              v-text="item.icon"
            ></v-icon>
          </v-list-item-avatar>
          <v-list-item-title v-text="item.text"></v-list-item-title>
        </v-list-item>
      </template>
    </v-list>
  </div>
</template>

<script>
import Writing from '~/components/Term.vue'
export default {
  data () {
    return {
      writing: false,
      slider: { label: 'thumb-color', val: 50, color: 'red', min: '0', max: '100' },
      bpm: 40,
      interval: null,
      isPlaying: false,
      dialog: false,
      step: 1,
    }
  },
  computed: {
    color () {
      if (this.bpm < 100) return 'indigo'
      if (this.bpm < 125) return 'teal'
      if (this.bpm < 140) return 'green'
      if (this.bpm < 175) return 'orange'
      return 'red'
    },
    animationDuration () {
      return `${60 / this.bpm}s`
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
    setIncrement() {
      this.step++
    },
  },
  components: {
    Writing,
  }
}
</script>

<style module>

.outlineDots {
  border: 3px dashed #ccc !important;
}

</style>
