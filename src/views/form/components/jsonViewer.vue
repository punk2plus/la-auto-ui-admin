<template>
  <div class="jsonViewer">
    <h2>json信息查看</h2>
    <json-viewer
      v-if="formConfig && formConfig.formItemList && formConfig.formItemList.length>0"
      :value="formConfig"
      :expand-depth="10"
      copyable
    ></json-viewer>
  </div>
</template>

<script>
export default {
  props: {
    formConfig: {
      type: Object,
      default: () => {}
    }
  },
  created() {
    this.$store.dispatch({
      type: "hello/getHello"
    });
  },
  methods: {
    gotoAbout() {
      this.$router.push("./about/1");
    }
  }
};
</script>

<style  lang="less">
.jsonViewer {
  width: 500px;
  height: 100%;
  h2 {
    margin-left: 20px;
  }
}
</style>
