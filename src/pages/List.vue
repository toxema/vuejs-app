<template>
  <div class="row bg-light shadow-sm my-2">
    <table class="table table-striped table-hover">
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
</template>

<script>
export default {};
</script>