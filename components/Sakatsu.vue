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
      dark
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
      <div id="container"></div>
      <v-toolbar-items>
        <v-btn
          dark
          text
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
        <v-card-title>最新のサ活</v-card-title>
          <v-card
            :loading="loading"
            class="mx-auto my-12"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <img
              height="250"
              src="~/static/images/sauna/sauna_01.jpg"
            />

            <v-card-title>Sauna One</v-card-title>

            <v-card-text>
              <v-row
                align="center"
                class="mx-0"
              >
                <v-rating
                  :value="4.5"
                  color="amber"
                  dense
                  half-increments
                  readonly
                  size="14"
                ></v-rating>

                <div class="grey--text ms-4">
                  4.5 (413)
                </div>
              </v-row>

              <div class="my-4 text-subtitle-1">
                $ • Italian, Cafe
              </div>

              <div>Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating.</div>
            </v-card-text>

            <v-divider class="mx-4"></v-divider>

            <v-card-title>Tonight's availability</v-card-title>

            <v-card-text>
              <v-chip-group
                v-model="selection"
                active-class="deep-purple accent-4 white--text"
                column
              >
                <v-chip>5:30PM</v-chip>

                <v-chip>7:30PM</v-chip>

                <v-chip>8:00PM</v-chip>

                <v-chip>9:00PM</v-chip>
              </v-chip-group>
            </v-card-text>

            <v-card-actions>
              <v-btn
                color="deep-purple lighten-2"
                text
                @click="reserve"
              >
                Reserve
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
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

// progressbar.js@1.0.0 version is used
// Docs: http://progressbarjs.readthedocs.org/en/1.0.0/

var bar = new ProgressBar.Circle(container, {
  color: '#aaa',
  // This has to be the same size as the maximum width to
  // prevent clipping
  strokeWidth: 4,
  trailWidth: 1,
  easing: 'easeInOut',
  duration: 1400,
  text: {
    autoStyleContainer: false
  },
  from: { color: '#aaa', width: 1 },
  to: { color: '#333', width: 4 },
  // Set default step function for all animate calls
  step: function(state, circle) {
    circle.path.setAttribute('stroke', state.color);
    circle.path.setAttribute('stroke-width', state.width);

    var value = Math.round(circle.value() * 100);
    if (value === 0) {
      circle.setText('');
    } else {
      circle.setText(value);
    }

  }
});
bar.text.style.fontFamily = '"Raleway", Helvetica, sans-serif';
bar.text.style.fontSize = '2rem';

bar.animate(1.0);  // Number from 0.0 to 1.0
</script>

<style module>

.outlineDots {
  border: 3px dashed #ccc !important;
}

</style>
