<template>
  <div
    class="drawer-background"
    :class="{ show: active }"
    @click="$emit('close-product-drawer')"
  ></div>
  <div class="drawer" :class="{ show: active }">
    <div class="drawer-close" @click="$emit('close-product-drawer')">X</div>

    <div class="product-details" v-if="product">
      <h3 class="text-center">{{ product.name }}</h3>
      <p class="description">{{ product.description }}</p>
      <h3 class="text-center">${{ product.price.toFixed(2) }}</h3>

      <div class="cart-total" v-if="product_total">
        <h3>In Cart</h3>
        <h4>{{ product_total }}</h4>
      </div>

      <div class="button-container">
        <button class="remove" @click="removeFromCart()">Remove</button>
        <button class="add" @click="addToCart()">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  emits: ["close-product-drawer"],
  props: ["product", "active"],
  computed: {
    product_total() {
      return this.$store.getters.productQuantity(this.product);
    },
  },
  methods: {
    addToCart() {
      this.$store.commit("addToCart", this.product);
    },
    removeFromCart() {
      this.$store.commit("removeFromCart", this.product);
    },
  },
};
</script>

<style lang="scss" scoped>
.drawer-background {
  width: 100vw;
  height: 100vh;
  position: fixed;
  left: 0;
  top: 0;
  background-color: rgba(125, 125, 125, 0.5);
  z-index: 100;
  display: none;
  transition: display 0.5s ease;

  &.show {
    display: block;
  }
}

.drawer {
  width: 95vw;
  height: 100vh;
  background-color: #8d86c9;
  position: fixed;
  top: 0;
  left: -105vw;
  padding: 15px;
  z-index: 101;
  transition: left 0.5s ease;
  overflow-y: scroll;
  color: #f7ece1;

  &.show {
    left: 0;
  }
}

.drawer-close {
  font-size: 1.2rem;
  padding: 5px;
  border-radius: 50%;
  right: 10px;
  border: 2px solid #242038;
  color: #242038;
  width: 20px;
  height: 20px;
  float: right;
  cursor: pointer;

  &:hover {
    background-color: lightgray;
  }
}

.product-details {
  display: flex;
  justify-content: center;
  flex-direction: column;

  p.description {
    padding: 20px;
    line-height: 1.5rem;
  }

  .button-container {
    button {
      width: 150px;
      border: none;
      padding: 10px;
      border-radius: 5px;
      margin: 0 5px 50px 5px;
      cursor: pointer;
    }
  }
}

@media (min-width: 600px) {
  .drawer {
    width: 450px;
  }
}
</style>
