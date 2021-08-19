
<template>
  <header>
    <nav class="navbar navbar-dark bg-dark">
      <!-- <button
        @click="show = !show"
        class="navbar-toggler btn btn-primary"
        data-bs-target="#navbarToggleExternalContent"
        type="button"
      >
        <span class="navbar-toggler-icon"></span>
      </button>-->
      <div class="text-center text-white">
        <h4>Equipment</h4>
      </div>
      <div class="text-center text-white navHover" @click="clickNav">Computer</div>
      <div class="text-center text-white navHover" @click="clickNav">Monitor</div>
      <div class="text-center text-white navHover" @click="clickNav">NB</div>
      <div class="text-center text-white"></div>
    </nav>
    <div class="collapse" id="navbarToggleExternalContent">
      <div class="bg-dark p-4">
        <h5 class="text-white h4">Collapsed content</h5>
        <span class="text-muted">Toggleable via the navbar brand.</span>
      </div>
    </div>
    <div class="container">
      <h2></h2>
    </div>
  </header>
</template>
<script>
import emitter from "../assets/js/mitt";

import { reactive, ref, watch } from "vue";

export default {
  name: "Demo",
  emits: ["hello"],
  setup() {
    // 數據
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = reactive({
      name: "馬克",
      age: 18,
      job: {
        j1: {
          salary: 30
        }
      }
    });

    // const sendChildB = () => {
    //   emitter.emit("send", msg);
    // };

    // 特殊情況
    watch(
      () => person.job,
      (newValue, oldValue) => {
        console.log("person的 job 變了 ", newValue, oldValue);
      },
      { deep: true }
    );

    function clickNav(e) {
      // console.log(e.target.innerText);
      // console.log(e);
      emitter.emit("hello", ref(e.target.innerText));
    }
    return {
      sum,
      msg,
      person,
      clickNav
    };
  }
};
</script>
