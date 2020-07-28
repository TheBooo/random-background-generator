<template>
  <div class="overlay">
    <div class="overlay-content">
      <div class="img-container">
        <img :src="picture.src.original" class="image" alt />
      </div>
      <div class="info-container">
        <button @click="$emit('closeOverlay')" class="btn">X</button>
        <div class="credit">
          Photo by
          <a
            :href="picture.photographer_url"
            target="_blank"
            class="credit-link"
          >{{picture.photographer}}</a>
        </div>
      </div>
    </div>
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
  justify-content: space-around;
  align-items: flex-start;
  padding: 1rem;
}
.img-container {
  width: 80%;
  height: 100%;
}
.image {
  width: auto;
  height: auto;
  max-height: 100%;
  max-width: 100%;
  box-shadow: 0px 0px 5px 1px rgba(0, 0, 0, 0.75);
}

.info-container {
  width: 20%;
  display: flex;
  flex-direction: column;
  justify-content: end;
}
.credit-link {
  cursor: pointer;
  font-weight: 600;
}
</style>