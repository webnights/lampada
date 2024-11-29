<template>
  <section class="products" ref="busesSection">
    <div class="container">
      <h2 class="title">Платные образовательные услуги</h2>
      <ul class="products__list">
        <Product
          v-for="(product, index) in products"
          :key="index"
          :product="product"
        />
      </ul>
    </div>
  </section>
</template>
<script>
import axios from "axios";
import Product from "/src/components/Product/Product.vue";
export default {
  components: { Product },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    async getProducts() {
      const response = await axios.get("http://localhost:3000/products");
      this.products = response.data;
      console.log(this.products)
    },
  },
  mounted() {
    this.getProducts();
  },
};
</script>
