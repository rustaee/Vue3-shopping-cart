<template>
  <div class="cart-item-card">
    <h3>Cart Total: ${{ cart_total.toFixed(2) }}</h3>
    <button class="view-product-button">Pay by credit card</button>
  </div>
</template>

<script>
export default {
  computed: {
    cart_total() {
      return this.$store.getters.cardTotal;
    },
  },
};
</script>

<style lang="scss" scoped>
.view-product-button {
  background: #9067c6;
  padding: 10px;
  outline: none;
  border: none;
  color: #fff;
  border-radius: 5px;
  letter-spacing: 1.5px;
  cursor: pointer;
}
</style>
