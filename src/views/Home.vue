<template>
  <div class="home">
    <ProductDescriptionDrawer
      :product="product"
      :active="active.product_drawer"
      @close-product-drawer="closeDrawer()"
    />
    <div class="product-cards-container">
      <ProductSummaryCard
        v-for="product in items"
        :key="product.id"
        :product="product"
        @view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
import items from "../data/items.js";
import ProductSummaryCard from "../components/products/ProductSummaryCard.vue";
import ProductDescriptionDrawer from "../components/products/ProductDescriptionDrawer.vue";

export default {
  name: "Home",
  components: { ProductSummaryCard, ProductDescriptionDrawer },

  data() {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false,
      },
    };
  },
  methods: {
    viewProduct(product) {
      this.product = product;
      this.active.product_drawer = true;
    },
    closeDrawer() {
      this.active.product_drawer = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.product-cards-container {
  padding: 20px;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
