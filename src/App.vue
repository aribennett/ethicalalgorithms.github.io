<template>
  <v-app v-resize="onResize">
    <v-row>
      <v-img :src="require('./assets/banner.jpg')" :height="windowSize.y * 0.6">
        <v-row fill-height>
          <v-col align="start" justify="center" class="pa-10">
            <h1
              v-bind:style="{ opacity: 1, fontSize: '50px' }"
              class="white--text"
            >
              Ari Bennett
            </h1>
            <h2 v-bind:style="{ opacity: 1 }" class="white--text">Portfolio</h2>
          </v-col>
        </v-row>
      </v-img>
    </v-row>
    <v-row>
      <Item
        :src="[
          require('./assets/img/1_resharp/1_rs.jpg'),
          require('./assets/img/1_resharp/2_rs.jpg'),
          require('./assets/img/1_resharp/3_rs.png'),
        ]"
        desc="Resharp Knife Sharpening"
        :interval="3"
      />
      <Item
        :src="[
          require('./assets/img/2_overshoot/1_os.jpg'),
          require('./assets/img/2_overshoot/2_os.jpg'),
          require('./assets/img/2_overshoot/3_os.gif'),
        ]"
        :interval="5"
        desc="Overshoot Casting Study"
      />
      <Item
        :src="[
          require('./assets/img/5_momentum/1_mt.jpg'),
          require('./assets/img/5_momentum/2_mt.gif'),
        ]"
        desc="Momentum Brushless Gyroscope"
      />
    </v-row>
    <v-row>
      <Item
        :src="[
          require('./assets/img/7_ked/1_kd.jpg'),
          require('./assets/img/7_ked/2_kd.jpg'),
        ]"
        desc="Knee Enhancement Device"
      />
      <Item
        :src="[
          require('./assets/img/3_tesselite/1_ts.jpg'),
          require('./assets/img/3_tesselite/2_ts.jpg'),
          require('./assets/img/3_tesselite/3_ts.jpg'),
        ]"
        desc="Tesselight Light Tiles"
      />
      <Item
        :src="[
          require('./assets/img/4_balance/1_bal.gif'),
          require('./assets/img/4_balance/2_bal.jpg'),
        ]"
        :interval="10"
        desc="Balance Inverted Pendulum"
      />
    </v-row>
    <v-row>
      <Item
        :src="[
          require('./assets/img/8_laser/1_ls.jpeg'),
          require('./assets/img/8_laser/2_ls.gif'),
        ]"
        :interval="10"
        desc="Desktop Laser Cutter"
      />
      <Item
        :src="[
          require('./assets/img/9_iron/1_ir.jpg'),
          require('./assets/img/9_iron/2_ir.jpg'),
        ]"
        desc="Custom Soldering Iron"
      />
      <Item
        :src="[
          require('./assets/img/6_lego/1_lg.jpg'),
          require('./assets/img/6_lego/2_lg.jpg'),
          require('./assets/img/6_lego/3_lg.jpg'),
          require('./assets/img/6_lego/4_lg.jpg'),
          require('./assets/img/6_lego/5_lg.jpg'),
          require('./assets/img/6_lego/6_lg.jpg'),
          require('./assets/img/6_lego/7_lg.jpg'),
          require('./assets/img/6_lego/8_lg.jpg'),
          require('./assets/img/6_lego/9_lg.jpg'),
          require('./assets/img/6_lego/10_lg.jpg'),
          require('./assets/img/6_lego/11_lg.jpg'),
          require('./assets/img/6_lego/12_lg.jpg'),
          require('./assets/img/6_lego/13_lg.jpg'),
          require('./assets/img/6_lego/14_lg.jpg'),
          require('./assets/img/6_lego/15_lg.jpg'),
          require('./assets/img/6_lego/16_lg.jpg'),
          require('./assets/img/6_lego/17_lg.jpg'),
          require('./assets/img/6_lego/18_lg.jpg'),
        ]"
        desc="LEGO Machine Shop"
        :interval="1.5"
      />
    </v-row>
    <v-row>
      <Item
        :src="[
          require('./assets/img/10_kiwi/1_ki.jpg'),
          require('./assets/img/10_kiwi/2_ki.jpg'),
        ]"
        desc="Kiwi Keyless Entry"
      />
      <Item
        :src="[
          require('./assets/img/11_tt/2_tt.jpg'),
          require('./assets/img/11_tt/1_tt.jpg'),
        ]"
        desc="Touch Torch Flashlight"
      />
      <Item
        :src="[
          require('./assets/img/12_218/1_218.jpg'),
          require('./assets/img/12_218/2_218.jpg'),
        ]"
        desc="Graduate Mechatronics"
      />
    </v-row>
    <v-row>
      <Item
        :src="[require('./assets/img/13_orb/1_orb.jpg')]"
        desc="3D Printed Lighting"
      />
      <Item
        :src="[require('./assets/img/14_silicone/1_si.jpg')]"
        desc="Candy Molds"
      />
      <Item
        :src="[
          require('./assets/img/15_way/1_way.jpg'),
          require('./assets/img/15_way/2_way.jpg'),
        ]"
        desc="Digital Wayfinder"
      />
    </v-row>
  </v-app>
</template>

<script>
import Item from "./components/Item";
export default {
  name: "App",

  components: {
    Item,
  },

  data: () => ({
    windowSize: {
      x: 0,
      y: 0,
    },
    hovered: false,
    activeTile: "",
  }),
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
  },
};
</script>
