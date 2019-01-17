<template>
  <div id="app">
    <form @submit.prevent="onSubmit()">
      <input name="newProduct" v-model="newProductName" v-validate="'required|min:3'">
      <button>Add</button>
      {{ msg }}
    </form>

    <ul>
      <li v-for="p in products" :key="p.id">{{ p.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "app",
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
      newProductID: 2,
      newProductName: ""
    };
  },
  methods: {
    onSubmit() {
      this.products.push({
        id: this.newProductId++,
        name: this.newProductName
      });
      this.newProductName = "";
      this.$validator.reset();
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
