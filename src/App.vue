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
          <button @click="showLog()" class="btn btn-danger ml-1">HISTORY</button>
        </div>
      </div>
      <div class="row bg-light py-2 shadow-sm my-2">
        <!--  Table Verisi 
        <tanktable v-bind:data="data"/>
        -->
        <table class="table">
          <thead class="thead-dark">
            <tr>
              <th scope="col">#Dev ID</th>
              <th scope="col">Name</th>
              <th scope="col">Tank 1</th>
              <th scope="col">Tank 2</th>
              <th scope="col">Firm</th>
              <th scope="col">Last Update</th>
              <th scope="col">Data</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(tank,index) in tanks" v-bind:key="tank.uid">
              <th scope="row">#{{index}}</th>
              <td>{{tank.name}}</td>
              <td class="text-danger">
                <h3>%{{tank.tank1}}</h3>
              </td>
              <td class="text-danger">
                <h3>%{{tank.tank2}}</h3>
              </td>
              <td>{{tank.firm}}</td>
              <td>{{tank.last_update}}</td>
              <td class="text-right">
                <button @click="showLog()" class="btn btn-danger ml-1">LOG</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      tanks: []
    };
  },
  methods: {
    get() {
      axios
        .get("http://rezonansmuhendislik.com/webcloud/servis.php?cmd=getAll")
        .then(res => {
          console.log(res.data);
          this.tanks = res.data;
        });
    },
    showLog() {
      console.log("get All Tank Logs");
    }
  },
  mounted() {
    console.log("mounted app");
    this.get();
  }
};
</script>