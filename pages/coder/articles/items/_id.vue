<template>
  <div class="box">
    <el-row class="box-1">
      <div class="title">
        <h2>{{item_title}}</h2>
      </div>
    </el-row>
    <el-row class="box-2">
      <div class="mavonEditor">
        <no-ssr>
          <mavon-editor
            class="mavonEditor"
            v-model="md"
            previewBackground="rgb(195, 183, 183)"
            :editable="false"
            :toolbarsFlag="false"
            :shortCut="false"
            :ishljs="false"
            defaultOpen="preview"
          />
        </no-ssr>
      </div>
    </el-row>
  </div>
</template>

<script>
// 引入marked 解析md
// import marked, { options } from "marked";
// 引入highlight 代码高亮
// import hljs from "highlight.js";
// import "~/assets/css/dark.css";
// import "~/assets/css/atom-one-light.scss";
// 引入markdown-it
// import markdownit from "markdown-it";

export default {
  data() {
    return {};
  },
  async asyncData({ params, $axios }) {
    const { id } = params;
    const res = await $axios.$get(`coderitemMd/${id}`);
    const { index, item_title, md, title, username } = res.data;
    // // 配置marked
    // let renderer = new marked.Renderer();
    // renderer.code = function(code, language) {
    //   return (
    //     '<pre><code class="hljs ' +
    //     language +
    //     '">' +
    //     hljs.highlightAuto(code).value +
    //     "</code></pre>"
    //   );
    // };
    // marked.setOptions({
    //   renderer: renderer,
    //   pedantic: false, //只解析符合Markdown定义的，不修正Markdown的错误。填写true或者false
    //   gfm: true, //启动类似Github样式的Markdown,填写true或者false
    //   breaks: true, //支持Github换行符，必须打开gfm选项，填写true或者false
    //   sanitize: false, //原始输出，忽略HTML标签，这个作为一个开发人员，一定要写flase
    //   smartLists: true, //优化列表输出，这个填写ture之后，你的样式会好看很多，所以建议设置成ture
    //   smartypants: false,
    //   tables: false, //支持Github形式的表格，必须打开gfm选项
    //   xhtml: true
    // });
    // const mdHtml = marked(md);
    return {
      index,
      item_title,
      md,
      title,
      username
    };
  }
};
</script>

<style lang="scss">
.box {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  border-radius: 10px;
  padding: 10px;
  overflow: hidden;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
}
.box-1 {
  height: 10%;
}
.box-2 {
  height: 90%;
}
.title {
  text-align: center;
  line-height: 1;
  color: #000;
}
.mavonEditor {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 15px;
  .v-note-edit {
    display: none;
  }
  .v-note-show {
    width: 100% !important;
    -webkit-flex: 0 0 100% !important;
  }
  .v-show-content {
    padding: 30px !important;
  }
}
</style>