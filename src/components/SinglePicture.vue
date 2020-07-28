<template>
  <div class="overlay">
    <div class="overlay-content"></div>
  </div>
</template>

<script>
export default {
  name: "SinglePicture",
  props: ["picture"],
  created() {
    console.log(this.picture);
  },
};
</script>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background: rgba(231, 226, 221, 0.8);
  z-index: 2;

  display: flex;
  justify-content: center;
  align-items: center;
}
.overlay-content {
  width: 70%;
  height: 70%;
  background-color: #fff;
  display: flex;
}
</style>