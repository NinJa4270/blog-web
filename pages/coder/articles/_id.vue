<template>
  <div class="box">
    <div class="centent">
      <div class="card" v-for="item in items" :key="item.id">
        <div class="card-image">
          <img :src="info.cover" />
          <div class="index">Post {{item.index}}</div>
        </div>
        <div class="card-title">
          <span>{{info.title}}</span>
          <h2>{{item.item_title}}</h2>
        </div>
        <div class="card-icons">
          <div class="icons" style="border-right:2px solid white">
            <div class="icon">data</div>
            <div class="type">{{item.createTime}}</div>
          </div>
          <div class="icons">
            <nuxt-link class="link" :to="`/coder/articles/items/${item.id}`">
              <i class="el-icon-more"></i>
              <div class="type">ReadMore</div>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
    <div class="navigate">
      <div @click="lastPage">
        <i class="el-icon-caret-top"></i>
      </div>
      <div>{{queryInfo.pageNum}}/{{allNum}}</div>
      <div @click="nextPage">
        <i class="el-icon-caret-bottom"></i>
      </div>
      <div style="font-size:20px">Total:{{total}}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      queryInfo: {
        pageSize: 8,
        pageNum: 1,
        allNum: 1
      }
    };
  },
  async asyncData({ params, $axios, app }) {
    const { id } = params;
    const queryInfo = {
      pageSize: 8,
      pageNum: 1
    };
    // 章节列表
    const res = await $axios.$get(`coderitems/${id}`, {
      params: {
        query: queryInfo
      }
    });
    const total = res.total;
    let allNum = Math.ceil(total / 8);
    // 文章信息
    const article = await $axios.$get(`articles/${id}`);
    const items = res.data;
    const info = article.data[0];
    items.forEach(element => {
      element.createTime = app.onlyDate(element.createTime);
    });
    return {
      id,
      info,
      items,
      queryInfo: {
        pageSize: 8,
        pageNum: 1
      },
      total,
      allNum
    };
  },
  methods: {
    // 获取上一页数据
    async lastPage() {
      // 先判断是否有上一
      if (this.queryInfo.pageNum <= 1) {
        this.$message.error({ message: "没有上一页了", duration: "2000" });
      } else {
        this.queryInfo.pageNum -= 1;
        const res = await this.$axios.$get(`coderitems/${this.id}`, {
          params: {
            query: this.queryInfo
          }
        });
        res.data.forEach(element => {
          element.createTime = this.$onlyDate(element.createTime);
        });
        this.items = res.data;
        this.$message.success({
          message: `第${this.queryInfo.pageNum}页`,
          duration: "2000"
        });
      }
    },
    // 获取下一页数据
    async nextPage() {
      // 判断是否有下一页
      if (this.queryInfo.pageNum < this.allNum) {
        this.queryInfo.pageNum += 1;
        const res = await this.$axios.$get(`coderitems/${this.id}`, {
          params: {
            query: this.queryInfo
          }
        });
        console.log(res);
        res.data.forEach(element => {
          element.createTime = this.$onlyDate(element.createTime);
        });
        this.items = res.data;
        this.$message.success({
          message: `第${this.queryInfo.pageNum}页`,
          duration: "2000"
        });
      } else {
        this.$message.error({ message: "没有下一页了", duration: "2000" });
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.box {
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.3);
  box-sizing: border-box;
  border-radius: 10px;
  padding: 30px;
  overflow: hidden;
  display: flex;
}
.navigate {
  position: absolute;
  right: 3%;
  top: 50%;
  transform: translate(0, -50%);
  font-size: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.centent {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
}
.card {
  width: 330px;
  height: 360px;
  display: grid;
  grid-template-columns: 330px;
  grid-template-rows: 180px 100px 80px;
  grid-template-areas: "image" "title" "icons";
  border-radius: 18px;
  background: white;
  box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.9);
  text-align: center;
  margin: 0 10px 20px 10px;
  transition: 0.5s;
}

.card-image {
  grid-area: image;
  position: relative;
  .index {
    position: absolute;
    top: 10px;
    right: 10px;
    background: rgba(255, 255, 255, 0.3);
    color: black;
    font-weight: 700;
  }
  img {
    width: 100%;
    height: 100%;
    display: block;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
  }
}
.card-title {
  grid-area: title;
  margin-top: 10px;
  margin-bottom: 0;
  color: black;
  span {
    color: rgb(255, 7, 110);
    font-size: 13px;
  }
  h2 {
    margin: 0;
    font-size: 28px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
  }
}
.link {
    text-decoration: none;
    color: white;
}
.card-icons {
  grid-area: icons;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
  background-color: #4d8798;

  .icons {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 10px;
    .icon {
      font-size: 11px;
      font-weight: 300;
      text-transform: uppercase;
    }
    .type {
      font-size: 22px;
      font-weight: 500;
    }
  }
}
.card:hover {
  transform: scale(1.1);
  box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.6);
}
</style>