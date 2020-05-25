<template>
  <div class="mavonEditor">
    <no-ssr>
      <mavon-editor
        class="mavonEditor"
        v-model="md"
        previewBackground="grey"
        :editable="false"
        :toolbarsFlag="false"
        :shortCut="false"
        defaultOpen="preview"
      />
    </no-ssr>
  </div>
</template>

<script>
export default {
  data() {
    return {
      handbook: "#### how to use mavonEditor in nuxt.js"
    };
  },
  async asyncData({$axios}){
    const res = await $axios.$get(`coderitemMd/20`);
    const { index, item_title, md, title, username } = res.data;
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
.mavonEditor {
  width: 50vw;
  height: 50vh;
}

.mavonEditor {
    display: flex;
    justify-content: center;
    align-items: center;
  .v-note-edit {
    display: none;
  }
  .v-note-show {
      width: 100% !important;
      -webkit-flex: 0 0 100% !important;
  }
  
}
</style>
