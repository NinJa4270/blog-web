<template>
  <div class="box-others">
    <el-carousel :interval="4000" type="card" height="500px">
      <el-carousel-item v-for="item in items" :key="item.id">
        <!-- <h3 class="medium">{{ item.id }}</h3> -->
        <nuxt-link :to="item.to">
          <img class="swiper-img" :src="item.src" />
        </nuxt-link>
        {{item.src}}
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  async asyncData() {
    return {
      items: [
        {
          id: 1,
          src: require("@/assets/img/swiper/1.jpg"),
          to: "/coder/others/cat"
        },
        {
          id: 2,
          src: require("@/assets/img/swiper/2.jpeg"),
          to: "/coder/others/soccer"
        },
        {
          id: 3,
          src: require("@/assets/img/swiper/3.jpeg"),
          to: "/coder/others/basketball"
        },
        {
          id: 4,
          src: require("@/assets/img/swiper/4.jpg"),
          to: "/coder/others/game"
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
.box-others {
  width: 100%;
  height: 100%;
  overflow: hidden;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;

  .el-carousel {
    width: 90%;
  }
  .swiper-img {
    width: 100%;
    height: 100%;
    border-radius: 15px;
    transition: 0.5s;
  }
  .swiper-img:hover {
    transform: scale(1.2);
    box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.6);
  }
}
</style>