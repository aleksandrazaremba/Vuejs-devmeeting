<template>
  <div>
    <ul>
      <li v-for="p in products" :key="p.id">{{ p.name }}</li>
    </ul>
    <p v-if="!products.length">No products!</p>
  </div>
</template>

<script>
export default {
  name: "ProductList",
  props: {
    products: {
      type: Array
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
