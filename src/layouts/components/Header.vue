<template>
  <el-header class="Header">
    <div class="title">{{ $route.meta.title || '--' }}</div>
  </el-header>
</template>

<script>
export default {
  created() {
    // console.log(this.$route.meta.)
  }
};
</script>

<style lang="less">
.title {
  line-height: 60px;
}
</style>
