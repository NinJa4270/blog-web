<template>
  <div class="bg">
    <img src="~@/assets/img/mario.jpg" class="gamer" />
    <img src="~@/assets/img/code.jpg" class="code" />
    <nuxt-link class="text-gamer to-page" to="/gamer">Go To Gamer</nuxt-link>
    <nuxt-link class="text-coder to-page" to="/coder">Go To Coder</nuxt-link>
  </div>
</template>

<script>
export default {
  layout: "index",
  components: {}
};
</script>

<style lang="scss" scoped>
.bg {
  width: 100vw;
  height: 100vh;
  top: 0;
  position: absolute;
  .gamer {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    clip-path: polygon(0 0, 36% 0, 64% 100%, 0% 100%);
    outline: none;
    border: 0;
    display: block;
    width: 100%;
    height: 100%;
  }
  .code {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    clip-path: polygon(100% 0, 36% 0, 64% 100%, 100% 100%);
    outline: none;
    border: 0;
    display: block;
    width: 100%;
    height: 100%;
  }
  .text-gamer {
    position: absolute;
    padding: 10px 30px;
    top: 8%;
    left: 8%;
    z-index: 9;
    color: white;
    font-size: 2em;
  }
  .text-coder {
    position: absolute;
    padding: 10px 30px;
    bottom: 8%;
    right: 8%;
    z-index: 9;
    color: white;
    font-size: 2em;
  }
  .to-page {
    text-decoration: none;
    text-transform: uppercase;
    background: #25ccf7;
    border-radius: 20px;
  }
}
</style>
