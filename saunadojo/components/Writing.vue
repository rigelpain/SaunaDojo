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
            sm="6"
            md="4"
          >
            <v-text-field
              label="Legal first name*"
              required
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="6"
            md="4"
          >
            <v-text-field
              label="Legal middle name"
              hint="example of helper text only on focus"
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="6"
            md="4"
          >
            <v-text-field
              label="Legal last name*"
              hint="example of persistent helper text"
              persistent-hint
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              label="Email*"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              label="Password*"
              type="password"
              required
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
          >
            <Term />
          </v-col>
          <v-col
            cols="12"
            sm="6"
          >
            <v-select
              :items="['0-17', '18-29', '30-54', '54+']"
              label="Age*"
              required
            ></v-select>
          </v-col>
          <v-col
            cols="12"
            sm="6"
          >
            <v-autocomplete
              :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
              label="Interests"
              multiple
            ></v-autocomplete>
          </v-col>
        </v-row>
      </v-container>
      <small>*indicates required field</small>
    </v-card-text>
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
