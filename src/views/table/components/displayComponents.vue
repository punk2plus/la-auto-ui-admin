<template>
  <div class="displayComponents">
    <c-auto-create-form
      v-if="formConfig && formConfig.formItemList && formConfig.formItemList.length>0"
      v-model="here"
      :form-config="formConfig"
    />
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
  data() {
    return {
      here: {}
    };
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
.displayComponents {
  flex: 1;
  height: 100%;
  border-right: 1px solid #ccc;
}
</style>
