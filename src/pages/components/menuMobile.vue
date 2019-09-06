<template>
  <div>
    <el-menu>
      <el-menu-item  index="1">
        <i class="el-icon-menu"></i>
        <span slot="title">关于我</span>
      </el-menu-item>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">技术掌握</span>
      </el-menu-item>
      <el-menu-item index="3">
        <i class="el-icon-document"></i>
        <span slot="title">作品展示</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">联系我</span>
      </el-menu-item>
    </el-menu>
  </div>
</template>

<script>
export default {
  name: 'MenuMobile'
}
</script>

<style lang="stylus" scoped>

</style>
