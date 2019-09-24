<template>
  <div>
    <div class="fix-top bg-dark px-1 py-1">
      <h3 class="text-white">Rezonans | Vue Dashboard</h3>
    </div>
    <div class="container">
      <div class="row bg-light px-1 py-2 shadow-sm">
        <div class="col-lg-8">
          <h3>Tank Listesi</h3>
        </div>
        <div class="col-lg-4 text-right">
          <button @click="get()" class="btn btn-success">GET ALL</button>
          <button @click="login()" class="btn btn-danger ml-1">LOGIN</button>
        </div>
      </div>

      <tanklist v-if="tanklistgoster" />
      <Login v-if="logingoster" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import List from "./pages/List.vue";
import Login from "./pages/Login.vue";
export default {
  components: {
    tanklist: List,
    Login
  },
  data() {
    return {
      tanks: [],
      logingoster: false,
      tanklistgoster: true
    };
  },
  methods: {
    get() {
      this.tanklistgoster = true;
      this.logingoster = false;
      axios
        .get("http://rezonansmuhendislik.com/webcloud/servis.php?cmd=getAll")
        .then(res => {
          console.log(res.data);
          this.tanks = res.data;
        });
    },
    login() {
      this.tanklistgoster = false;
      this.logingoster = true;
    }
  },
  mounted() {
    console.log("mounted app");
    this.get();
  }
};
</script>