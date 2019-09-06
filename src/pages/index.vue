<template>
  <div>
    <el-container>
      <el-header>
        <index-header-mobile></index-header-mobile>
        <index-header-pc></index-header-pc>
      </el-header>
      <el-main>
        <index-info></index-info>
      </el-main>
    </el-container>
  </div>
</template>

<script>
import IndexHeaderMobile from './components/headerMobile'
import IndexHeaderPc from './components/headerPc'
import IndexInfo from './components/info'
export default {
  name: 'Index',
  data () {
    return {
    }
  },
  components: {
    IndexHeaderMobile,
    IndexHeaderPc,
    IndexInfo
  }
}
</script>

<style lang="stylus" scoped>
  .el-header
    height 1rem !important
    padding 0
  .el-main
    padding 0
</style>
