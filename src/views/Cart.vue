<template>
  <section>
    <h1>Your Cart</h1>
    <CartItemCard
      v-for="product in products"
      :key="product.id"
      :product="product"
    />
    <CartSummaryPayment :products="products"/>
  </section>
</template>

<script>
import CartItemCard from "../components/cart/CartItemCard.vue";
import CartSummaryPayment from "../components/cart/CartSummaryPayment.vue";
export default {
  components: {CartItemCard, CartSummaryPayment},
  data() {
    return {};
  },
  computed: {
    products() {
      return this.$store.getters.cartItems;
    },
  },
};
</script>

<style lang="scss" scoped></style>
