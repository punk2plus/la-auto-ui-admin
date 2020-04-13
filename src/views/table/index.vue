<template>
  <div class="home">
    <el-tabs v-model="activeName" @tab-click="handleClick">
      <el-tab-pane label="配置" name="config">
        <div class="hom1e">
          <componentsViewer @addComponents="addComponents" />
          <displayComponents :formConfig="config" />
        </div>
        <jsonViewer :formConfig="config" />
      </el-tab-pane>
      <el-tab-pane label="预览" name="display">table display</el-tab-pane>
    </el-tabs>
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
import jsonViewer from "@/components/jsonViewer";

export default {
  components: {
    componentsViewer,
    displayComponents,
    jsonViewer
  },
  data() {
    return {
      config: config,
      activeName: "config"
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
    addComponents(data) {
      buttonItem.key = `${buttonItem.key}1`;
      this.config.formItemList.push(buttonItem);
    },
    handleClick() {
      
    }
  }
};
</script>



<style  lang="less">
.home {
  height: 100%;
  .hom1e {
    display: flex;
    min-height: 400px;
    border-bottom: 1px solid #ccc;
  }
}
</style>
