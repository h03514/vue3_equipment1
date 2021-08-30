<template>
  <div v-if="msg == 'Computer'">
    <div class="row Computer" v-for="(item, key) in equipment.computer" :key="key">
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
  <div v-if="msg == 'Monitor'">
    <div class="row Monitor" v-for="(item, key) in equipment.monitor" :key="key">
      <div class="col-sm-3">{{ item.qvesn }}</div>
      <div class="col-sm-2">{{ item.title }}</div>
      <div class="col-sm-3">{{ item.type }}</div>
      <div class="col-sm-3">{{ item.model }}</div>
      <div class="col-sm-1" @click="ddusios">
        <a href="javascript:;">aaa</a>
        <i class="fas fa-ad"></i>
      </div>
    </div>
  </div>
  <div>
    <hr v-if="abc">
    <div class="row" v-for="(item , index) in testOBj" :key="index">
      <div class="col-4">{{item.gender}}</div>
      <div class="col-4">{{item.name.first}}</div>
      <div class="col-4">{{item.name.last}}</div>
    </div>
  </div>
</template>

<script>
import emitter from "../assets/js/mitt";
import axios from "axios";
import { ref, reactive, onMounted } from "vue";

export default {
  name: "testEmit2",
  data() {
    return {
      testOBj: {},
      abc: false
    };
  },
  methods: {
    async ddusios() {
      await axios.get("https://randomuser.me/api/?results=5").then(res => {
        this.testOBj = res.data.results;
        this.abc = true;
      });
    }
  },

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

    emitter.on("hello", val => {
      msg.value = val.value;
    });

    emitter.on("send", val => {
      msg.value = val.value;
    });
    emitter.on("ddd", val => {
      wer.value = val.value;
    });

    const state = reactive({
      hits: []
    });

    // function ddusios() {

    //   VueAxios({
    //     method: "get",
    //     url: "https://randomuser.me/api/"
    //   }).then(function(response) {
    //     return Object(response);
    //   });
    //   // const data = fetch("https://hn.algolia.com/api/v1/search?query=vue").then(
    //   //   (rsp) => {
    //   //     rsp.json();
    //   //     console.log(rsp);
    //   //   }
    //   // );
    //   // state.hits = data.hits;
    // }

    onMounted(async () => {});

    // emitter.emit("sss", reactive (ddusios));

    return {
      msg: msg,
      wer: wer,
      equipment,
      state
    };
  }
};
</script>
