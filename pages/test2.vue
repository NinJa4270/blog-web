<template>
  <div>
    <div class="card middle">
      <div class="front">
        <img src="../assets/img/mario.jpg" alt />
      </div>
      <div class="back">
        <div class="back-content middle">
          <h2>Coder</h2>
          <span>name</span>
          <div class="sm">
            <a href="#">
              <i class="el-icon-platform-eleme"></i>
            </a>
            <a href="#">
              <i class="el-icon-star-on"></i>
            </a>
            <a href="#">
              <i class="el-icon-s-help"></i>
            </a>
            <a href="#">
              <i class="el-icon-s-promotion"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
body {
  background-color: #333;
}
.middle {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.card {
  cursor: pointer;
  width: 340px;
  height: 480px;
}
.front,
.back {
  width: 100%;
  height: 100%;
  overflow: hidden;
  backface-visibility: hidden;
  position: absolute;
  transition: transform 0.6s linear;
}
img {
  height: 100%;
}
.front {
  transform: perspective(600px) rotateY(0deg);
}
.back {
  background: #f1f1f1;
  transform: perspective(600px) rotateY(180deg);
}
.back-content {
  color: #2c3e50;
  text-align: center;
  width: 100%;
}
.sm {
  margin: 20px 0;
}
a {
  display: inline-flex;
  width: 40px;
  height: 40px;
  font: 18px;
  justify-content: center;
  align-items: center;
  color: #2c3e50;
  transition: 0.4s;
  border-radius: 50%;
  text-decoration: none;
}

a:hover {
  background: #2c3e50;
  color: white;
  text-decoration: none;
}
.card:hover > .front {
  transform: perspective(600px) rotateY(-180deg);
}
.card:hover > .back {
  transform: perspective(600px) rotateY(0deg);
}
</style>