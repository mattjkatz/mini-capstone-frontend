<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      products: {},
    };
  },
  created: function () {
    this.productsIndex();
  },
  methods: {
    productsIndex() {
      axios.get("/products").then((response) => {
        console.log(response.data);
      });
    },
  },
};
</script>

<template>
  <div v-for="product in products" v-bind:key="product.id">
    <p>Product name {{ product.name }}</p>
  </div>
</template>

<style></style>
