<template>
  <div class="box">
    <div class="title">My Articles</div>
    <el-row class="card">
      <template v-for="item in items">
        <el-col :span="8" :key="item.id">
          <nuxt-link class="link" :to="`/coder/articles/${item.id}`">
            <el-image :src="item.cover"></el-image>
            <div class="introduce">
              <div class="title">{{item.title}}</div>
              <div class="content">{{item.introduce}}</div>
              <div class="info">
                <div>{{item.username}}</div>
                <div>{{item.createTime}}</div>
              </div>
            </div>
          </nuxt-link>
        </el-col>
      </template>
    </el-row>
    <el-row>
      <el-pagination
        @current-change="handleCurrentChange"
        :current-page="pageNum"
        :page-size="6"
        layout="total, prev, pager, next, jumper"
        :total="total"
      ></el-pagination>
    </el-row>
  </div>
</template>

<script>
export default {
  layout: "child",
  data() {
    return {
      queryInfo: {
        query: "",
        pageSize: 6,
        pageNum: 1
      }
    };
  },
  async asyncData({ $axios, app }) {
    const queryInfo = {
      query: "",
      pageSize: 6,
      pageNum: 1
    };
    const res = await $axios.$get("articles", {
      params: {
        query: queryInfo
      }
    });
    const items = res.data;
    const total = res.total;
    const pageNum = res.page;
    items.forEach(element => {
      element.createTime = app.onlyDate(element.createTime);
    });
    return {
      items,
      total,
      pageNum
    };
  },
  methods: {
    handleCurrentChange(newPage) {
      this.queryInfo.pageNum = newPage;
      this.getArticles();
    },
    // 请求文章列表
    async getArticles() {
      const res = await this.$axios.$get("articles", {
        params: {
          query: this.queryInfo
        }
      });
      res.data.forEach(element => {
        element.createTime = this.$onlyDate(element.createTime);
      });
      this.items = res.data;
      this.total = res.total;
      this.pageNum = res.page;
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
  padding: 10px;
}
.title {
  margin: 10px 0;
  font-size: 30px;
  font-weight: 700;
  display: flex;
  justify-content: center;
  align-items: center;
}
.card {
  width: 100%;
  height: 84%;

  .el-col {
    height: 50%;
    box-sizing: border-box;
    padding: 10px;
    border-top-right-radius: 15px;
    border-top-left-radius: 15px;
    .el-image {
      width: 100%;
      height: 70%;
      display: block;
      border-top-right-radius: 15px;
      border-top-left-radius: 15px;
    }
    .introduce {
      width: 100%;
      height: 30%;
      background-color: whitesmoke;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: 2px;
      .title {
        color: black;
        font-weight: 700;
        margin: 0;
        font-size: 16px;
      }
      .content {
        text-indent: 10px;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
        color: grey;
      }
      .info {
        padding: 5px;
        display: flex;
        justify-content: space-between;
        color: lightsalmon;
      }
    }
  }
}
.link {
  text-decoration: none;
}
.el-pagination {
  width: 360px;
  background-color: white;
  border-radius: 10px;
  display: flex;
  justify-content: flex-end;
  margin: 10px 0;
}
</style>
