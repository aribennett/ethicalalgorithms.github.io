<template>
  <v-img
    v-resize="onResize"
    :src="getSrc"
    :width="windowSize.x"
    :height="windowSize.y"
    @mouseenter.native="onHover(true)"
    @mouseleave.native="onHover(false)"
  >
    <v-row
      v-if="hovered"
      align="end"
      justify="center"
      class="fill-height pa-0"
      no-gutters
    >
      <v-row v-if="hasAlbum">
        <v-btn text v-on:click="rotateImage(false)" :height="windowSize.y/3">
          <v-icon right color="grey"> mdi-arrow-left </v-icon>
        </v-btn>
        <v-spacer />
        <v-btn text v-on:click="rotateImage(true)" :height="windowSize.y/3">
          <v-icon left color="grey"> mdi-arrow-right </v-icon>
        </v-btn>
      </v-row>
      <v-footer class="ma-0" :width="windowSize.x" color="rgb(0, 0, 0, 0.3)">
        <h4 class="white--text">
          {{ desc }}
        </h4>
      </v-footer>
    </v-row>
  </v-img>
</template>

<script>
export default {
  name: "Item",

  data: () => ({
    hovered: false,
    windowSize: {
      x: 0,
      y: 0,
    },
    currentImage: 0,
    rotateTimer: null,
  }),
  props: {
    src: Array,
    desc: String,
    interval: {
      type: Number,
      default: 3,
    },
  },
  methods: {
    onResize() {
      if (window.innerWidth > window.innerHeight) {
        this.windowSize = {
          x: window.innerWidth / 3,
          y: window.innerWidth / 4,
        };
      } else {
        this.windowSize = {
          x: window.innerWidth,
          y: window.innerWidth/1.3,
        };
      }
    },
    onHover(state) {
      this.hovered = state;
    },
    rotateImage(bool) {
      if (bool) {
        ++this.currentImage;
        this.currentImage %= this.src.length;
      } else {
        --this.currentImage;
        if (this.currentImage < 0) {
          this.currentImage = this.src.length + this.currentImage;
        }
      }
    },
  },
  computed: {
    getSrc() {
      return this.src[this.currentImage];
    },
    hasAlbum() {
      return(this.src.length > 1)
    }
  },
};
</script>
