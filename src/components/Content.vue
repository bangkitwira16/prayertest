<template>
  <div class="content component">
    <v-container>
      <v-row>
        <v-col><h2>Muharram 1442</h2></v-col>
        <v-col class="my-auto">
          <h3 class="text-right font-weight-light">September 2020</h3>
        </v-col>
      </v-row>
      <v-card>
        <v-container class="pa-2">
          <v-row>
            <v-col><h3 class="text-center">Sen</h3></v-col>
            <v-col><h3 class="text-center">Sel</h3></v-col>
            <v-col><h3 class="text-center">Rab</h3></v-col>
            <v-col><h3 class="text-center">Kam</h3></v-col>
            <v-col><h3 class="text-center">Jum</h3></v-col>
            <v-col><h3 class="text-center">Sab</h3></v-col>
            <v-col><h3 class="text-center">Min</h3></v-col>
          </v-row>
          <v-row>
            <v-col class="py-0 text-center"><h3>10</h3></v-col>
            <v-col class="py-0 text-center"><h3>11</h3></v-col>
            <v-col class="py-0 text-center"><h3>12</h3></v-col>
            <v-col class="py-0 text-center"><h3>13</h3></v-col>
            <v-col class="py-0 text-center"><h3>14</h3></v-col>
            <v-col class="py-0 text-center"><h3>15</h3></v-col>
            <v-col class="py-0 text-center"><h3>16</h3></v-col>
          </v-row>
          <v-row>
            <v-col class="py-0 text-center"><h4>1</h4></v-col>
            <v-col class="py-0 text-center"><h4>2</h4></v-col>
            <v-col class="py-0 text-center"><h4>3</h4></v-col>
            <v-col class="py-0 text-center"><h4>4</h4></v-col>
            <v-col class="py-0 text-center"><h4>5</h4></v-col>
            <v-col class="py-0 text-center"><h4>6</h4></v-col>
            <v-col class="py-0 text-center"><h4>7</h4></v-col>
          </v-row>
        </v-container>
      </v-card>
      <v-container>
        <v-card
          class="prayer-time mb-3"
          v-for="(prayer, index) in prayerData"
          v-bind:key="index"
        >
          <v-container class="py-0">
            <v-row>
              <v-col class="my-auto">
                <img
                  :src="require(`@/assets/images/${prayer.icon}`)"
                  alt=""
                /><span class="ml-2">{{ prayer.name }}</span>
              </v-col>
              <v-col class="text-right">
                <span>{{ prayer.time }}</span>
                <img
                  src="../assets/images/Path 185@1X.png"
                  alt=""
                  srcset=""
                  class="ml-2"
                />
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-container>
    </v-container>
  </div>
</template>
<script>
import PrayerData from "../assets/json/data.json";
export default {
  data: () => ({
    prayerData: PrayerData.data,
    path: "../assets/images/",
  }),
  mounted() {
    console.log(this.prayerData);
  },
  methods: {
    getImgUrl(icon) {
      return require("../assets/images" + icon);
    },
  },
};
</script>
<style lang="scss" scoped>
span {
  color: #7e7eda;
  font-size: 14px;
}
.v-card.prayer-time {
  background: #ededfa;
  border-radius: 20px !important;
}
</style>