<template>
  <div>
    <el-menu>
      <a href="/" class="title">
        <el-menu-item index="1">
          <i class="iconfont iconblogger"></i>
          <span slot="title">关于我</span>
        </el-menu-item>
      </a>
      <a href="https://github.com/NCR7777" class="title" target="_blank">
        <el-menu-item index="2">
          <i class="iconfont icongithub"></i>
          <span slot="title">Github</span>
        </el-menu-item>
      </a>
      <a href="http://www.ncrlhym.cn" class="title" target="_blank">
        <el-menu-item index="3">
          <i class="iconfont iconicon_Notepad"></i>
          <span slot="title" class="title">我的博客</span>
        </el-menu-item>
      </a>
      <a href="mailto: ncr019@163.com" class="title">
        <el-menu-item index="4">
          <i class="iconfont iconicon_Email"></i>
          <span slot="title" class="title">联系我</span>
        </el-menu-item>
      </a>
    </el-menu>
  </div>
</template>

<script>
export default {
  name: 'MenuMobile'
}
</script>

<style lang="stylus" scoped>
  .title
    color #000
</style>
