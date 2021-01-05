<template>
  <div id="nav" v-if="showNav">
    <router-link :to="{ name: 'Home' }">Home</router-link> |
    <router-link :to="{ name: 'About' }">About</router-link> |
    <router-link :to="{ name: 'Jobs' }">Jobs</router-link>
  </div>
  <router-view />
</template>

<script>
export default {
  name: "App",
  computed: {
    currentRoute() {
      return this.$route.name;
    },
    showNav() {
      if (this.currentRoute == "JobDetails") {
        return false;
      }
      return true;
    },
  },
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

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  padding: 10px;
  border-radius: 999px;
}

#nav a.router-link-exact-active {
  color: white;
  background-color: crimson;
}
</style>
