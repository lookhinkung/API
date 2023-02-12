<script setup>
import axios from "axios";
import { ref } from "vue";
const data = ref();
const config = {
  method: "get",
  url: "https://dummyjson.com/products",
  headers: {},
};
axios(config)
  .then(function (response) {
    data.value = response.data.products;
    console.log(data.value);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>
<template>
  <div class="container">
    <h1>Store Api</h1>
    <table class="table table-bordered table-hover">
      <thead class="thead-light">
        <th>Picture</th>
        <th>Name</th>
        <th>Brand</th>
        <th>Price</th>
      </thead>
      <tbody>
        <tr v-for="(value, index) in data" :key="index">
          <td><img :src="value.thumbnail" alt="" /></td>
          <td>{{ value.title }}</td>
          <td>{{ value.brand }}</td>
          <td>{{ value.price }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style scoped>
.container {
  padding: 20px;
}
</style>
