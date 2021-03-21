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
    }
  },
  methods: {
    onResize() {
      if (window.innerWidth > window.innerHeight) {
        this.windowSize = {
          x: window.innerWidth / 3,
          y: window.innerHeight / 2.5,
        };
      } else {
        this.windowSize = {
          x: window.innerWidth,
          y: window.innerHeight / 2.5,
        };
      }
    },
    onHover(state) {
      this.hovered = state;
      if (this.hovered) {
        this.rotateTimer = setInterval(this.rotateImage, this.interval * 1000);
      } else {
        clearInterval(this.rotateTimer);
        this.currentImage = 0;
      }
    },
    rotateImage() {
      ++this.currentImage;
      this.currentImage %= this.src.length;
    },
  },
  computed: {
    getSrc() {
      return this.src[this.currentImage];
    },
  },
};
</script>
