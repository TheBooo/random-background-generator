<template>
  <div id="app">
    <Pics />
  </div>
</template>

<script>
import Pics from "./components/Pics";

export default {
  name: "App",
  components: { Pics }
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
