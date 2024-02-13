<template>
  <div id="app">
    <open-screen v-if="page === 0" @next-page="nextPage"></open-screen>
    <reception v-if="page === 1" @next-page="nextPage"></reception>
    <hand-id v-if="page === 2" @next-page="nextPage"></hand-id>
    <main-page v-if="page === 3" @next-page="nextPage"></main-page>
  </div>
</template>
 
<script>
import OpenScreen from "@/components/OpenScreen.vue";
import Reception from "@/components/Reception.vue";
import HandId from "@/components/HandId.vue";
import MainPage from "@/components/MainPage.vue";

export default {
  name: "app",
  components: {
    OpenScreen,
    Reception,
    HandId,
    MainPage,
  },
  data() {
    return {
      page: 0,
    }
  },

  methods: {
    nextPage() {
      this.page++;
    }
  }
};
</script>

<style>
@font-face {
    font-family: Karantina;
    src: url("assets/fonts/Karantina-Regular.ttf");
  }
  
  body,
  html {
    margin: 0;
    padding: 0;
    height: 100%;
    overflow: hidden;
    font-family: "Karantina";
    direction: rtl;
    background-color: #f4f1de;
  }</style>