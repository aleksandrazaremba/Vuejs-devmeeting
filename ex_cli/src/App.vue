<template>
  <div id="app">
    <product-list :products="products"></product-list>
    <add-product @add-product="onAddProduct"></add-product>
  </div>
</template>

<script>
import ProductList from "./components/ProductList";
import AddProduct from "./components/AddProduct";

export default {
  name: "App",
  components: {
    ProductList,
    AddProduct
  },
  data() {
    return {
      msg: "Add your product name",
      products: [
        {
          id: 0,
          name: "Carrot"
        },
        {
          id: 1,
          name: "Apple"
        }
      ]
      // ,
      // newProductId: 2,
      // newProductName: ""
    };
  },
  methods: {
    onAddProduct(product) {
      this.products.push(product);
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
