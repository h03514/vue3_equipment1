<template>
  <div class="row">
    <div class="col-sm-3 fw-bolder fs-5 titleName">SN</div>
    <div class="col-sm-2 fw-bolder fs-5 titleName">姓名</div>
    <div class="col-sm-3 fw-bolder fs-5 titleName">類別</div>
    <div class="col-sm-3 fw-bolder fs-5 titleName">型號</div>
    <div class="col-sm-1 fw-bolder fs-5 titleName"></div>
  </div>
  <!-- <div>
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
  <div v-if="sss=='Monitor'">
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
  </div>-->
  <div>{{title}}</div>
</template>

<script>
import mitt from "mitt";

import { reactive, ref } from "vue";

export default {
  name: "Main",
  props: ["msg", "title"],
  setup(props) {
    let sss = reactive({ props });
    const ddds = ref("123");
    const emitter = mitt();
    // console.log(sss);
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
      console.log(val);
    });

    function isShow(e) {
      if (e == "Computer") {
        console.log("a");
        document.querySelector(".Computer");
      }
      if (e == "Monitor") {
        console.log("b");
        document.querySelector(".Monitor");
      }
    }
    return {
      equipment,
      isShow,
      sss,
      ddds
    };
  }
};
</script>
