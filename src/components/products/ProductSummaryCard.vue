<template>
  <div class="card">
    <h3>{{ product.name }}</h3>
    <h5 class="price">Price: ${{ product.price.toFixed(2) }}</h5>
    <p class="description">Description: {{ description }}</p>
    <p class="text-muted">{{ product.category }}</p>
    <button class="view-product-button" @click="$emit('view-product', product)">
      View Product
    </button>
  </div>
</template>

<script>
export default {
  props: ["product"],
  data() {
    return {};
  },
  computed: {
    description() {
      return this.product.description.substring(0, 150) + "...";
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  width: 80%;
  margin: 10%;
  padding: 10px;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
  .price {
    color: #8d86c9;
  }

  .description {
    font-size: 0.85rem;
    text-align: justify;
  }

  .text-muted {
    color: #ccc;
  }

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
}

@media (min-width: 600px) {
  .card {
    width: 270px;
    margin: 10px 0;
  }
}
</style>
