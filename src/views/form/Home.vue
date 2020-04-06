<template>
  <div class="home">
    <componentsViewer @addComponents="handlClick" />
    <displayComponents :formConfig="config"/>
    <jsonViewer :formConfig="config"/>
  </div>
</template>

<script>
const buttonItem = {
  type: "select",
  label: "状态",
  value: "",
  disabled: false,
  multiple: false,
  placeholder: "请选择",
  rules: [],
  key: "selectValue",
  options: {
    UNSOLVED: "未解决",
    SOLVED: "已解决"
  }
};

const config = {
  inline: false,
  labelPosition: "right",
  labelWidth: "80px",
  size: "small",
  statusIcon: true,
  formItemList: []
};

import componentsViewer from "./components/componentsViewer";
import displayComponents from "./components/displayComponents";
import jsonViewer from "./components/jsonViewer";

export default {
  components: {
    componentsViewer,
    displayComponents,
    jsonViewer
  },
  data() {
    return {
      config: config,
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
    },
    handlClick(data) {
      buttonItem.key = `${buttonItem.key}1`;
      this.config.formItemList.push(buttonItem);
    }
  }
};
</script>



<style  lang="less">
.home {
  display: flex;
  height: 100%;
}
</style>
