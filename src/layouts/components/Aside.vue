<template>
  <div class="Aside">
    <el-aside style="width: 200px;">
      <el-menu :default-openeds="['form']" @select="handleSelect">
        <el-menu-item index="form">
          <template slot="title">
            <i class="el-icon-message"></i>form
          </template>
        </el-menu-item>
        <el-menu-item index="table">
          <template slot="title">
            <i class="el-icon-message"></i>table
          </template>
        </el-menu-item>
      </el-menu>
    </el-aside>
  </div>
</template>

<script>
export default {
  computed: {},
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
      this.$router.push(`/${key}`)
    }
  }
};
</script>

<style lang="less">
.Aside {
  height: 100%;
  border-right: solid 1px #e6e6e6;
  .el-menu {
    border-right: 0px;
  }
}
</style>
