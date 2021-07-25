<template>
  <div class="ma-5">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
    <template v-slot:activator="{ on, attrs }">
      <!-- <v-btn
        depressed
        block
        class="d-flex justify-center mb-6"
        :class="$style.outlineDots"
        height="150px"
        v-bind="attrs"
        v-on="on"
      >
        新しくサ活を記録する
      </v-btn> -->
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
        <Writing />
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>


    <v-card>
      <v-row no-gutters>
        <v-col cols="9">
          <v-card-title>最新のサ活</v-card-title>
        </v-col>
      </v-row>
    </v-card>
    <v-card>
      <v-card-title>過去のベストサ活</v-card-title>
    </v-card>

  </div>
</template>

<script>
import Writing from '~/components/Writing.vue'
export default {
  data () {
      return {
        writing: false,
        dialog: false,
      }
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
