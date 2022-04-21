<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      products: [],
    };
  },
  created: function () {
    this.productsIndex();
  },
  methods: {
    productsIndex() {
      axios.get("/products").then((response) => {
        console.log(response.data);
        this.products = response.data;
        console.log(this.products.images);
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>All Products</h1>
    <div v-for="product in products" v-bind:key="product.id">
      <h3>{{ product.name }}</h3>
      <p>{{ product.description }} | ${{ product.price }}</p>
      <p>{{ product.images[0] }}</p>
      <img v-if="!!product.images[0]" v-bind:src="product.images[0].url" v-bind:alt="product.name" />
    </div>
  </div>
</template>

<style></style>
