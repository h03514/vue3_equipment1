<template>
  <h3>childA组件传过来的msg: {{ wer }}</h3>
  <div v-if="msg=='computer'">
    <div class="row Computer" v-for="(item,key) in equipment.computer" :key="key">
      <div class="col-sm-3">{{ item.qvesn }}</div>
      <div class="col-sm-2">{{ item.title }}</div>
      <div class="col-sm-3">{{ item.type }}</div>
      <div class="col-sm-3">{{ item.model }}</div>
      <div class="col-sm-1">
        <a href="javascript:;">aaa</a>
        <i class="fas fa-ad"></i>
      </div>
    </div>
  </div>
  <div v-if="msg=='monitor'">
    <div class="row Monitor" v-for="(item,key) in equipment.monitor" :key="key">
      <div class="col-sm-3">{{ item.qvesn }}</div>
      <div class="col-sm-2">{{ item.title }}</div>
      <div class="col-sm-3">{{ item.type }}</div>
      <div class="col-sm-3">{{ item.model }}</div>
      <div class="col-sm-1">
        <a href="javascript:;">aaa</a>
        <i class="fas fa-ad"></i>
      </div>
    </div>
  </div>
</template>

<script>
import emitter from "../assets/js/mitt";
import { ref, reactive } from "vue";

export default {
  name: "testEmit2",
  setup() {
    let msg = ref("");
    let wer = ref("");

    let equipment = reactive({
      computer: [
        {
          id: 1,
          qvesn: "216911001",
          title: "supperlier-01",
          type: "computer",
          model: "520MT"
        },
        {
          id: 2,
          qvesn: "216911002",
          title: "supperlier-02",
          type: "computer",
          model: "520MT"
        },
        {
          id: 3,
          qvesn: "216911003",
          title: "supperlier-03",
          type: "computer",
          model: "520MT"
        }
      ],
      monitor: [
        {
          id: 1,
          qvesn: "216911004",
          title: "supperlier-04",
          type: "Monitor",
          model: "ViewSonic"
        },
        {
          id: 2,
          qvesn: "216911005",
          title: "supperlier-05",
          type: "Monitor",
          model: "Benq"
        },
        {
          id: 3,
          qvesn: "216911006",
          title: "supperlier-06",
          type: "Monitor",
          model: "AOC"
        }
      ]
    });

    emitter.on("send", val => {
      msg.value = val.value;
    });
    emitter.on("ddd", val => {
      wer.value = val.value;
    });
    return {
      msg: msg,
      wer: wer,
      equipment
    };
  }
};
</script>
