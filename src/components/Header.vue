<template>
  <div class="top title">
    <v-alert type="info" v-for="(time, index) in matchTime" v-bind:key="index"
      >Sudah masuk waktu <span class="font-weight-bold">{{ time.name }}</span
      >, Solat dulu yuk.
    </v-alert>
    <v-container class="top-title">
      <!-- {{ prayerNow }}
      {{ currentIndex }}
      {{ nextPrayer }} -->
      <!-- {{ curTotalTime }} -->
      <v-row>
        <v-col>
          <h1>Waktu Shalat</h1>
        </v-col>
        <v-col class="mt-auto">
          <ul>
            <li><h3 class="text-right">Jakarta Pusat</h3></li>
          </ul>
        </v-col>
      </v-row>
    </v-container>
    <div class="content">
      <img
        src="../assets/images/header.png"
        width="100%"
        alt=""
        srcset=""
        class="top-abs"
      />
      <div class="time-content">
        <h1 class="timer">{{ timeNow }}</h1>
        <h3 class="prayer">
          Next Prayer
          <span
            class="font-weight-bold"
            v-if="curTotalTime > 42600 && curTotalTime < 54300"
            >Terbit 05:43</span
          >
          <span
            class="font-weight-bold"
            v-else-if="curTotalTime > 54300 && curTotalTime < 114600"
            >Dzuhur 11:46</span
          >
          <span
            class="font-weight-bold"
            v-else-if="curTotalTime > 114600 && curTotalTime < 145700"
            >Asar 14:57</span
          >
          <span
            class="font-weight-bold"
            v-else-if="curTotalTime > 145700 && curTotalTime < 174900"
            >Magrib 17:49</span
          >
          <span
            class="font-weight-bold"
            v-else-if="curTotalTime > 174900 && curTotalTime < 185800"
            >Isya 18:58</span
          >
          <span class="font-weight-bold" v-else>Subuh 04:26</span>
        </h3>
      </div>
    </div>
    <div></div>
  </div>
</template>
<script>
import moment from "moment";
import PrayerData from "../assets/json/data.json";
export default {
  data: () => ({
    timeNow: "",
    prayerData: PrayerData.data,
    matchTime: null,
    prayerNow: "",
    curTime: null,
    curTotalTime: null,
    currentIndex: null,
    nextPrayer: null,
  }),
  mounted() {
    this.timer();
  },
  methods: {
    timer() {
      var self = this;
      this.timeNow = moment().locale("id").format("HH:mm:ss");
      this.matchTime = this.prayerData.filter(
        (prayer) => prayer.time === this.timeNow
      );
      console.log(this.matchTime);
      if (this.matchTime.length > 0) {
        this.prayerNow = this.matchTime[0].name;
        this.currentIndex = this.prayerData
          .map((e) => e.name)
          .indexOf(this.prayerNow);
        this.nextPrayer = this.prayerData[this.currentIndex + 1];
      }
      setInterval(self.timer, 1000);
      console.log(this.timeNow);
      this.curTime = this.timeNow.split(":");
      this.curTotalTime = this.curTime[0] + this.curTime[1] + this.curTime[2];
      this.curTotalTime.toString();
      if (this.curTotalTime.charAt(0) === "0") {
        this.curTotalTime.substring(1);
      }
      console.log("cur", this.curTotalTime);
      parseInt(this.curTime);
      console.log(this.prayerNow);
    },
  },
};
</script>
<style lang="scss" scoped>
ul {
  list-style: none;
  line-height: 0;
}
ul li::before {
  content: "\2022";
  color: #7e7eda;
  font-weight: bold;
  display: inline-block;
  width: 1em;
  margin-left: 30%;
}
.top-title {
  position: relative;
  z-index: 1;
}
img.top-abs {
  position: relative;
  z-index: 0;
  margin-top: -35px;
  padding: 0 10px;
}
.content {
  position: relative;
}
.time-content {
  top: 0;
  margin-left: 20px;
  margin-top: 10px;
  position: absolute;
  h3 {
    line-height: 1;
    font-weight: normal;
  }
}
@media (min-width: 1281px) {
  .time-content {
    margin-top: 275px;
  }
  ul li::before {
    margin-left: 58%;
  }
}
@media only screen and (min-width: 768px) and (max-width: 1280px) {
  .time-content {
    margin-top: 125px;
  }
  ul li::before {
    margin-left: 58%;
  }
}
@media only screen and (min-width: 375px) and (max-width: 767px) {
  .time-content {
    margin-top: 15px;
  }
  ul li::before {
    margin-left: 40%;
  }
}
</style>