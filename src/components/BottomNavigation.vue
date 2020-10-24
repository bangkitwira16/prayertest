<template>
  <div id="nav">
    <v-bottom-navigation :value="value" color="indigo" grow fixed>
      <v-btn class="mt-auto mb-auto">
        <span>Home</span>

        <v-icon>mdi-home</v-icon>
      </v-btn>

      <v-btn class="mt-auto mb-auto"> 
        <span>Shalat</span>

        <v-icon>mdi-moon-waning-crescent</v-icon>
      </v-btn>

      <v-btn class="mt-auto mb-auto">
        <span>Quran</span>

        <v-icon>mdi-book-open-page-variant</v-icon>
      </v-btn>

      <v-btn class="mt-auto mb-auto">
        <span>Profile</span>

        <v-icon>mdi-account-circle</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </div>
</template>
<script>
export default {
  name: "BottomNav",
  data: () => ({ value: 1 }),
};
</script>