<template>
  <div class="row">
    <div class="col-sm-3 fw-bolder fs-5 titleName">SN</div>
    <div class="col-sm-2 fw-bolder fs-5 titleName">姓名</div>
    <div class="col-sm-3 fw-bolder fs-5 titleName">類別</div>
    <div class="col-sm-3 fw-bolder fs-5 titleName">型號</div>
    <div class="col-sm-1 fw-bolder fs-5 titleName"></div>
  </div>
  <div class="row" v-for="(item,key) in equipment.computer" :key="key">
    <div class="col-sm-3">
      {{ item.qvesn }}
    </div>
    <div class="col-sm-2">
      {{ item.title }}
    </div>
    <div class="col-sm-3">
      {{ item.type }}
    </div>
    <div class="col-sm-3">
      {{ item.model }}
    </div>
    <div class="col-sm-1"></div>
  </div>
</template>

<script>
import { reactive } from "vue";

export default {
  name: "Main",
  setup() {
    let equipment = reactive({
      computer: [
        {
          id: 1,
          qvesn: "216911001",
          title: "supperlier-01",
          type: "computer",
          model: "520MT",
        },
        {
          id: 2,
          qvesn: "216911002",
          title: "supperlier-02",
          type: "computer",
          model: "520MT",
        },
        {
          id: 3,
          qvesn: "216911003",
          title: "supperlier-03",
          type: "computer",
          model: "520MT",
        },
      ],
      monitor: [
        {
          id: 1,
          qvesn: "216911004",
          title: "supperlier-04",
          type: "Monitor",
          model: "ViewSonic",
        },
        {
          id: 2,
          qvesn: "216911005",
          title: "supperlier-05",
          type: "Monitor",
          model: "Benq",
        },
        {
          id: 3,
          qvesn: "216911006",
          title: "supperlier-06",
          type: "Monitor",
          model: "AOC",
        },
      ],
    });
    let msg = reactive("你好ddd啊");
    return {
      msg,
      equipment,
    };
  },
};
</script>
