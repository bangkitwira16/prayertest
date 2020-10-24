<template>
  <v-app>
    <Header />
    <v-main>
      <div class="main">
        <Content />
        <BottomNavigation />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header";
import Content from "./components/Content";
import BottomNavigation from "./components/BottomNavigation";

export default {
  name: "App",

  components: {
    Header,
    Content,
    BottomNavigation,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
@import "./assets/css/style.scss";
</style>