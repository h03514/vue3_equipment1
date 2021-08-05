
<template>
  <header>
    <nav class="navbar navbar-dark bg-dark">
      <button @click="show = !show" class="navbar-toggler btn btn-primary" type="button">
        <span class="navbar-toggler-icon"></span>
      </button>
      <p class="text-center text-white">Equipment Management</p>
      <div class="text-center text-white"></div>
    </nav>
    <div class="container">
      <h2></h2>
    </div>
  </header>
</template>
<script>
import { reactive, ref, watch } from "vue";

export default {
  name: "Demo",
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

    // 特殊情況
    watch(
      () => person.job,
      (newValue, oldValue) => {
        console.log("person的 job 變了 ", newValue, oldValue);
      },
      { deep: true }
    );
    return {
      sum,
      msg,
      person
    };
  }
};
</script>
