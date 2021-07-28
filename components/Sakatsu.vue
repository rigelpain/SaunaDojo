<template>
  <div class="ma-5">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
      style="z-index: 100;"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          class="ma-2 px-5 v-btn--fixed v-size--large"
          rounded
          large
          dark
          color="saunaWrite"
          v-bind="attrs"
          v-on="on"
          style="z-index: 100; bottom: 100px; right: 30px;"
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

    <v-row>
      <v-col cols="12">
        <p class="text-h6">最新のサ活</p>
        <Card1 />
      </v-col>
    </v-row>

    <v-divider class="mt-10"></v-divider>

    <v-row class="mt-10">
      <v-col>
        <p class="text-h6">過去のベストサ活</p>
        <Card2 />
      </v-col>
    </v-row>

  </div>
</template>

<script>
import Writing from '~/components/Writing.vue'
import Card1 from '~/components/Card1.vue'
import Card2 from '~/components/Card2.vue'

export default {
  data () {
      return {
      }
    },
  computed: {
  },
  components: {
    Writing,
    Card1,
    Card2,
  }
}

</script>

<style>

</style>



