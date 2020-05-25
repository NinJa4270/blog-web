<template>
  <el-container>
    <img src="~@/assets/img/coder-index.jpg" class="bk" />
    <el-header>My Code In Blog</el-header>
    <el-main>
      <el-row :gutter="20">
        <el-col :span="4">
          <div class="left-content">
            <nuxt-link to="/coder/home">1</nuxt-link>
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
</template>

<script>
export default {};
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
    background-color: rgba(88, 88, 88, 0.8);
    border-radius: 20px;
    margin: 10px 10px;
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 40px;
    color: white;
  }
  .el-main {
    width: 100%;
    height: 90%;
    padding: 1%;
    .el-row,
    .el-col {
      height: 100%;
    }
    .left-content {
      height: 100%;
    }
    .right-content {
      height: 100%;
    }
  }
}
</style>