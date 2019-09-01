<template>
  <div id="app">
    <Header />
    <Search />
    <Home />
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Header from "./components/Header.vue";
import Search from "./components/Search";

export default {
  name: "app",
  components: {
    Header,
    Home,
    Search
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  background: rgba(219, 217, 217, 0.8);
  padding: 0;
  margin: 0;
}
</style>
