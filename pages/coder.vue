
<template>
  <div class="bg">
    <el-container>
      <img src="~@/assets/img/code.jpg" class="bk" />
      <el-header>
        <div class="header-light">NinJa Blog</div>
        <div class="header-right">
          <a href="https://github.com/731391599">
            <fa :icon="['fab', 'github']" />Github
          </a>
          <a href="https://gitee.com/yq770770">
            <fa :icon="['fab', 'google']" />Gitee
          </a>
          <a href="https://yq427.cn">
            <fa :icon="['fas', 'home']" />Home
          </a>
        </div>
      </el-header>
      <el-main>
        <el-row :gutter="20">
          <el-col :span="4">
            <div class="left-content">
              <div class="navigate-bar">
                <div class="ul" v-for="item in items" :key="item.text">
                  <div class="li">
                    <span>&gt;</span>
                    <nuxt-link class="to-Page" :to="item.link" :data-text="item.text">{{item.text}}</nuxt-link>
                  </div>
                </div>
              </div>
            </div>
          </el-col>
          <el-col :span="20">
            <div class="right-content">
              <nuxt-child />
            </div>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<script >
export default {
  data() {
    return {
      items: [
        { link: "/", text: "Home" },
        { link: "/coder", text: "Coder Home" },
        { link: "/coder/articles", text: "My Articles" },
        { link: "/coder/videos", text: "Favorite videos" },
        { link: "/coder/others", text: "Ohters" },
        { link: "/coder/me", text: "Contact Me" }
      ]
    };
  },
  async asyncData() {}
};
</script>

<style lang="scss" scoped>
.el-container {
  height: 100vh;
  .bk {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    outline: none;
    border: 0;
    display: block;
    width: 100%;
    height: 100%;
  }
  .el-header {
    background-color: rgba(0, 0, 0, 0.1);
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 40px;
    color: white;
    .header-light {
      letter-spacing: 2px;
    }
    .header-right {
      display: flex;
      justify-content: center;
      align-items: center;
      letter-spacing: 2px;
      a {
        margin-right: 10px;
        font-size: 20px;
        text-decoration: none;
        color: white;
      }
    }
  }
  .el-main {
    box-sizing: border-box;
    width: 100%;
    height: 90%;
    padding: 1%;
    .el-row,
    .el-col {
      height: 100%;
    }
    .left-content {
      height: 90%;
    }
    .right-content {
      height: 100%;
    }
  }
}
.li {
  font-size: 28px;
  margin: 20px 20px;
}
span {
  position: relative;
  top: -2px;
  left: -10px;
  color: transparent;
}
.li:hover span {
  color: #ef0448;
}
.to-Page {
  position: relative;
  color: rgba(255, 255, 255, 0.1);
  text-decoration: none;
  font-weight: 700;
}
.to-Page:before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  overflow-y: hidden;
  color: #ffd700;
  white-space: nowrap;
  overflow: hidden;
}

.ul:hover .li .to-Page:before {
  animation: animate 0.5s steps(11) forwards;
}
@keyframes animate {
  0% {
    width: 214.328px;
  }
  100% {
    width: 0px;
  }
}
.ul .li:hover .to-Page:before {
  animation: animate2 2s steps(11) forwards;
}
@keyframes animate2 {
  0% {
    width: 0;
  }
  100% {
    width: 214.328px;
  }
}
</style>