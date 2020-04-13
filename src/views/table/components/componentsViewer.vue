<template>
  <div class="componentsViewer">
    <el-tabs v-model="activeName" @tab-click="handleClick">
      <el-tab-pane label="添加组件" name="first">
        <el-button
          class="components-item"
          v-for="(item,index)  in supportComponents"
          :key="index"
          round
          @click="handleClick1(item.name)"
        >{{item.name}}</el-button>
      </el-tab-pane>
      <el-tab-pane label="组件配置" name="second">组件配置</el-tab-pane>
      <el-tab-pane label="全局配置" name="third">全局配置</el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
const supportComponents = [
  { name: "普通" },
  { name: "formater" },
  { name: "dict" },
  { name: "solt" }
];

export default {
  data() {
    return {
      activeName: "first",
      supportComponents: supportComponents
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
    handleClick(tab, event) {
      console.log(tab, event);
    },
    handleClick1(name) {

      this.$emit('addComponents', name)
      console.log(name);
    }
  }
};
</script>


<style  lang="less">
.componentsViewer {
  width: 450px;
  min-height: 400px;
  border-right: 1px solid #ccc;
  .components-item {
    margin: 5px;
  }
}
</style>
