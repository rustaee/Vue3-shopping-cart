<template>
  <div id="nav">
    <router-link to="/" :class="{ active: $route.name === 'Home' }">
      Home
    </router-link>

    <router-link to="/mycart" :class="{ active: $route.name === 'Cart' }">
      Cart
    </router-link>
  </div>
  <router-view />
</template>
<script>
export default {
  mounted() {
    this.$store.commit("updateFromLocalStorage");
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #242038;
}

html,
body {
  margin: 0;
  padding: 0;
  overflow: hidden;
}

body {
  background-color: #f7ece1;
}

ul,
li {
  list-style: none;
}

a {
  text-decoration: none;
}

button:focus {
  outline: none;
}

button:focus {
  transform: scale(0.98);
}

button:hover {
  opacity: 0.9;
}

#nav {
  padding: 10px;
  width: 100%;
  height: 30px;
  background-color: #cac4ce;
  line-height: 30px;

  a {
    font-weight: bold;
    color: #262626;
    margin: 0 5px 0 5px;
    font-size: 1.25rem;

    &.active {
      color: #9067c6;
    }
  }
}

.text-center {
  text-align: center;
}
</style>
