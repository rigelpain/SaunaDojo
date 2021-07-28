<template>
  <v-card
    class="mx-auto"
  >
    <v-img v-bind:src="sauna_01" max-height="450px">
      <div class="card-inner px-2">
        <v-row align="center" class="ma-1">
          <v-col flex>
            <v-avatar
              size="50px"
            >
              <img
                alt="Avatar"
                src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
              >
            </v-avatar>
            <strong class="ml-2">admin</strong>
            <span class="ml-5 text-caption info--text">67.8kg</span>
            <span class="ml-5 text-caption info--text">173cm</span>
          </v-col>
          <v-col cols="2" class="text-subtitle-2 font-weight-light text--secondary">
            8h
          </v-col>
        </v-row>
        <v-divider></v-divider>
        <v-card-text>
          <v-row>
            <v-col class="mt-2 pb-0">
              <span
                class="text-caption font-weight-light"
              >
                総合スコア（ 3セット ）
              </span>
            </v-col>
            <v-col>
              <v-btn
                v-if="follow === false"
                color="saunaWrite"
                class="float-right"
                @click="follow = !follow"
              >
                弟子入り
              </v-btn>
              <v-btn
                v-if="follow === true"
                color="primary"
                class="float-right"
                @click="follow = !follow"
                outlined
              >
                師匠
              </v-btn>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <span class="text-h4 font-weight-light">
                72
              </span>
              <span class="subheading font-weight-light mr-1">pt</span>
              <v-fade-transition>
                <v-avatar
                  color="orange"
                  :style="{
                    animationDuration: '0.38s'
                  }"
                  class="mb-1 v-avatar--metronome"
                  size="12"
                ></v-avatar>
              </v-fade-transition>
            </v-col>
          </v-row>
          <v-row>
            <v-col class="pb-0">
              <span class="text-caption font-weight-light">
                最高セットスコア （ 2セット目 ）
              </span>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="4">
              <span class="text-h4 font-weight-light">
                82
              </span>
              <span class="subheading font-weight-light mr-1">pt</span>
              <v-fade-transition>
                <v-avatar
                  color="red"
                  :style="{
                    animationDuration: '0.27s'
                  }"
                  class="mb-1 v-avatar--metronome"
                  size="12"
                ></v-avatar>
              </v-fade-transition>
            </v-col>
            <v-col cols="8" class="d-flex justify-space-around">
              <div class="d-flex">
                <span
                  class="text-h4 font-weight-light"
                >10</span>
                <div class="ml-2">
                  <li>
                    <v-icon small class="d-flex align-center" color="sauna">fas fa-hot-tub</v-icon>
                  </li>
                  <li>
                    <span class="font-weight-light">分</span>
                  </li>
                </div>
              </div>
              <div class="d-flex">
                <span
                  class="text-h4 font-weight-light"
                >5</span>
                <div class="ml-2">
                  <li>
                    <v-icon small class="d-flex align-center" color="water">fas fa-tint</v-icon>
                  </li>
                  <li>
                    <span class="font-weight-light">分</span>
                  </li>
                </div>
              </div>
              <div class="d-flex">
                <span
                  class="text-h4 font-weight-light"
                >5</span>
                <div class="ml-2">
                  <li>
                    <v-icon small class="d-flex align-center" color="chair">fas fa-chair</v-icon>
                  </li>
                  <li>
                    <span class="font-weight-light">分</span>
                  </li>
                </div>
              </div>
            </v-col>
          </v-row>
          <div class="mt-8 text-h6">
            Sauna One <br>
          </div>
          <span class="text-subtitle-1">北海道函館市中道2-43-22</span>
          <v-chip-group
            column
          >
            <v-chip
              color="sauna"
              text-color="white"
              class="px-5"
              outlined
            >
              <v-icon small left class="mr-2">
                fas fa-hot-tub
              </v-icon>
              92℃
            </v-chip>
            <v-chip
              color="water"
              text-color="white"
              class="px-5"
              outlined
            >
              <v-icon small left class="mr-2">
                fas fa-tint
              </v-icon>
              8℃
            </v-chip>
            <v-chip
              color="chair"
              text-color="white"
              class="px-5"
              outlined
            >
              <v-icon small left class="mr-2">
                fas fa-chair
              </v-icon>
              3席
            </v-chip>
          </v-chip-group>
        </v-card-text>
      </div>
    </v-img>
  </v-card>
</template>


<script>
export default {
  data () {
      return {
        writing: false,
        dialog: false,
        bpm: 40,
        interval: null,
        isPlaying: true,
        follow: false,
        sauna_01: require("~/static/images/sauna/sauna_01.jpg"),
      }
    },
  computed: {
  }
}

</script>

<style>
.card-inner {
  backdrop-filter: blur(3px) brightness(0.4);
}

@keyframes heartBeatAnimation {
  from {
    transform: scale(.5);
  }

  to {
    transform: scale(1);
  }
}

</style>


