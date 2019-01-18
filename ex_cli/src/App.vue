<template>
  <div id="app">
    <product-list :products="products"></product-list>
    <form @submit.prevent="onSubmit()">
      <input name="product" v-model="newProductName" v-validate="'required|min:3'">
      <button>Add</button>
      {{ msg }}
      <div v-show="errors.has('product')">{{ errors.first('product') }}</div>
    </form>
    <ul>
      <li v-for="p in products" :key="p.id">{{ p.name }}</li>
    </ul>
    <p v-if="!products.length">No products!</p>
  </div>
</template>

<script>
import ProductList from "./components/ProductList";

export default {
  name: "App",
  components: {
    ProductList
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
      ],
      newProductId: 2,
      newProductName: ""
    };
  },
  methods: {
    onSubmit() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.products.push({
            id: this.newProductId++,
            name: this.newProductName
          });
          this.newProductName = "";
          this.$validator.reset();
        }
      });
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
