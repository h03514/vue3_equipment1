<template>
  <div>
    <button @click="sendChildB">向兄弟组件childB传值</button>
  </div>
</template>
<script>
import emitter from "../assets/js/mitt";
import { ref } from "vue";

export default {
  name: "testEmit1",
  setup() {
    const str = ref("组件A的数据dafsdfasdf信息");
    let equipment = ref("computer");

    const sendChildB = () => {
      if (equipment.value == "computer") {
        equipment.value = "monitor";
      } else {
        equipment.value = "computer";
      }
      emitter.emit("send", equipment);
      emitter.emit("ddd", str);
    };
    return {
      str,
      sendChildB,
      equipment
    };
  }
};
</script>
