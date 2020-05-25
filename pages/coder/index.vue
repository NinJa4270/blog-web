<template>
  <div class="box">
    <el-row>
      <el-col :span="8">
        <div class="card">
          <div class="front mid">
            <img src="../../assets/img/img1.jpg" />
          </div>
          <div class="back mid">
            <div class="back-content">
              <h2>项目</h2>
              <span>name</span>
            </div>
          </div>
        </div>
      </el-col>
      <el-col :span="8">
        <div class="card">
          <div class="front mid">
            <img src="../../assets/img/img2.jpg" />
          </div>
          <div class="back mid">
            <div class="back-content">
              <h2>源码</h2>
              <span>name</span>
            </div>
          </div>
        </div>
      </el-col>
      <el-col :span="8">
        <div class="card">
          <div class="front mid">
            <img src="../../assets/img/img3.png" />
          </div>
          <div class="back mid">
            <div class="back-content">
              <h2>Bug</h2>
              <span>name</span>
            </div>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  async asyncData({ $axios }) {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.box {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.el-row {
  width: 100%;
}
.el-col {
  display: flex;
  justify-content: center;
  align-items: center;
}
.card {
  cursor: pointer;
  height: 480px;
  width: 340px;
  position: relative;
}
.mid {
  position: absolute;
}
.front,
.back {
  width: 100%;
  height: 100%;
  overflow: hidden;
  backface-visibility: hidden;
  transition: transform 0.6s linear;
}
img {
  height: 100%;
  width: 100%;
  border-radius: 15px;
}
.front {
  transform: perspective(600px) rotateY(0deg);
}
.back {
  background: #f1f1f1;
  transform: perspective(600px) rotateY(180deg);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.back-content {
  color: #2c3e50;
  text-align: center;
  width: 100%;
}
.card:hover > .front {
  transform: perspective(600px) rotateY(-180deg);
}
.card:hover > .back {
  transform: perspective(600px) rotateY(0deg);
}
</style>