<template>
  <div class="box">
    <div class="box-me">
      <img src="~/assets/img/1-1.jpg" alt />
      <h1>yq427.cn</h1>
        <ul>
          <li><fa :icon="['fab', 'weixin']" /> Wechat:niko731391599</li>
          <li><fa :icon="['fas', 'phone']" /> Tel:17398081021</li>
      </ul>
      <ul>
          <li><a href="https://github.com/731391599"><fa :icon="['fab', 'github']" /></a></li>
          <li><a href="https://gitee.com/yq770770"><fa :icon="['fab', 'google']" /></a></li>
          <li><a href="https://yq427.cn"><fa :icon="['fas', 'home']" /></a></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.box {
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.box-me{
    width: 450px;
    background: rgba(0,0,0,.4);
    padding: 40px;
    text-align: center;
    margin: auto;
    margin-top: 5%;
    color: white;
    img{
        border-radius: 50%;
        width: 200px;
        height: 200px;
    }
    h1{
        font-size: 40px;
        letter-spacing: 4px;
        font-weight: 100;
    }
    h5{
        font-size: 25px;
        letter-spacing: 1px;
        font-weight: 100;
    }
    p{
        text-align: justify;
    }
    ul{
        margin: 0;
        padding: 0;
    }
    li{
        display: inline-block;
        margin: 10px;
        list-style: none;
    }
    a{
        color: white;
        font-size: 40px;
        transition: all ease-in-out 250ms;
    }
    a:hover{
        color: #b9b9b9;
    }
}

</style>