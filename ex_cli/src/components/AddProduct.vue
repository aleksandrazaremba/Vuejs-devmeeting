<template>
  <form @submit.prevent="onSubmit()">
    <input name="product" v-model="newProductName" v-validate="'required|min:3'">
    <button>Add</button>
    <div v-show="errors.has('product')">{{ errors.first('product') }}</div>
  </form>
</template>

<script>
export default {
  name: "AddProduct",
  data() {
    return {
      newProductId: 2,
      newProductName: ""
    };
  },
  methods: {
    onSubmit() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.$emit("add-product", {
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
