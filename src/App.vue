<template>
  <div id="app">
    <Header />
    <Pics />
  </div>
</template>

<script>
import Pics from "./components/Pics";
import Header from "./components/layout/Header";

export default {
  name: "App",
  components: { Pics, Header }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
