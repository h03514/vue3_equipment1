<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld></HelloWorld> -->
  <Demo></Demo>
  <Main></Main>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Demo from "./components/demo.vue";
import Main from "./components/main.vue";
import "@/assets/scss/bootstrap.min.css";
import "@/assets/scss/test.scss";

export default {
  name: "App",
  components: {
    // HelloWorld,
    Demo,
    Main
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>


