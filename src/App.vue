<template>
  <nav>
    <router-link :to="homeLink">Home</router-link> |
    <router-link to="/login">Login</router-link> |
    <router-link :to="shopLink" @click="navigateToShop">Shopping Cart</router-link>     
  </nav>
  <router-view/>
</template>

<script>
export default {
  data() {
    return {
      isLoggedIn: false
    };
  },
  computed: {
    shopLink() {
      return this.isLoggedIn ? '/shop' : '/login'; 
    },
    homeLink() {
      return this.isLoggedIn ? '/home' : '/';
    }
  },
  methods: {
    navigateToShop(event) {
      if (!this.isLoggedIn && event.target.href.includes('/shop')) {
        event.preventDefault();
      }
    }
  }
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
  padding: 10px;
  background-color: aquamarine;
  border-radius: 5px;
}
</style>
