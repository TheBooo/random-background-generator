<template>
  <main>
    <section class="section">
      <!-- pics -->
      <div class="pictures-container">
        <img
          v-for="(picture, i) in pictures"
          :key="picture.id"
          :src="picture.src.large"
          @click="openPicture(i)"
          class="picture"
        />
      </div>
      <!-- end of pics -->

      <!-- loading icon -->
      <div v-if="pictures.length === 0" class="loading-container">
        <div class="lds-ring">
          <div></div>
          <div></div>
          <div></div>
          <div></div>
        </div>
      </div>
      <!-- end of loading icon -->
    </section>
    <SinglePicture v-if="picture !== ''" v-bind:picture="picture" v-on:closeOverlay="closeOverlay" />
  </main>
</template>

<script>
import SinglePicture from "./SinglePicture";

export default {
  name: "Pics",
  components: { SinglePicture },
  data() {
    return {
      pictures: [],
      picture: "",
    };
  },
  methods: {
    openPicture(i) {
      this.picture = this.pictures[i];
    },
    closeOverlay() {
      this.picture = "";
    },
  },
  async created() {
    const params = {
      method: "GET",
      headers: {
        Authorization: process.env.VUE_APP_API_KEY,
      },
    };
    const page = Math.floor(Math.random() * Math.floor(500)); //random page 0-500
    const url = `https://api.pexels.com/v1/curated/?page=${page}&per_page=9`;
    try {
      const response = await fetch(url, params);
      const data = await response.json();
      this.pictures = data.photos;
    } catch (error) {
      console.log(error);
    }
    //console.log(process.env.VUE_APP_API_KEY);
  },
};
</script>

<style scoped>
.loading-container {
  padding: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
/* laoding animation */
.lds-ring {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-ring div {
  box-sizing: border-box;
  display: block;
  position: absolute;
  width: 64px;
  height: 64px;
  margin: 8px;
  border: 8px solid #808080;
  border-radius: 50%;
  animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  border-color: #808080 transparent transparent transparent;
}
.lds-ring div:nth-child(1) {
  animation-delay: -0.45s;
}
.lds-ring div:nth-child(2) {
  animation-delay: -0.3s;
}
.lds-ring div:nth-child(3) {
  animation-delay: -0.15s;
}
@keyframes lds-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
/**/
.section {
  padding-top: 20px;
}
.pictures-container {
  min-height: calc(100vh - 88px);
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-gap: 20px;
}
.picture {
  max-width: 100%;
  max-height: 100%;
  width: 100%;
  height: 100%;
  object-fit: cover;
  box-shadow: 0px 0px 5px 1px rgba(0, 0, 0, 0.75);
  cursor: pointer;
  transition: all 0.2s linear;
}
.picture:hover {
  opacity: 0.6;
}
</style>