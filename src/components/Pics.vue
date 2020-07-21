<template>
  <main>
    <section>
      <!-- pics -->
      <div class="pictures-container"></div>
      <!-- end of pics -->

      <!-- loading icon -->
      <div v-if="pictures.length === 0" class="loading">
        <div class="lds-ring">
          <div></div>
          <div></div>
          <div></div>
          <div></div>
        </div>
      </div>
      <!-- end of loading icon -->
    </section>
  </main>
</template>

<script>
export default {
  name: "Pics",
  data() {
    return {
      pictures: []
    };
  },
  created() {
    console.log(process.env.VUE_APP_API_KEY);
  }
};
</script>

<style scoped>
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
</style>