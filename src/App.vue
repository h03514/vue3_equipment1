<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld></HelloWorld> -->
  <Demo @hello="showEquipmentData"></Demo>
  <Main :title="btnMsg.name"></Main>
  <!-- <testEmit1></testEmit1> -->
  <testEmit2></testEmit2>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Demo from "./components/demo.vue";
// import Main from "./components/main.vue";
// import testEmit1 from "./components/testEmit1.vue";
import testEmit2 from "./components/testEmit2.vue";
import "@fortawesome/vue-fontawesome";
import "@/assets/scss/bootstrap.min.css";
import "@/assets/scss/test.scss";
import { reactive } from "vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    Demo,
    // Main,
    // testEmit1,
    testEmit2
  },

  setup() {
    let btnMsg = reactive({
      name: "Computer"
    });
    function showEquipmentData(da) {
      // this.flag = !this.flag;'
      btnMsg.name = da;
    }
    return {
      showEquipmentData,
      btnMsg
    };
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


