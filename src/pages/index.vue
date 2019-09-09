<template>
  <div>
    <el-container>
      <el-header>
        <index-header-mobile></index-header-mobile>
        <index-header-pc></index-header-pc>
      </el-header>
      <el-main>
        <index-info-mobile></index-info-mobile>
        <index-info-pc></index-info-pc>
      </el-main>
      <el-footer>
        <index-footer></index-footer>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import IndexHeaderMobile from './components/headerMobile'
import IndexHeaderPc from './components/headerPc'
import IndexInfoMobile from './components/infoMobile'
import IndexFooter from './components/footer'
import IndexInfoPc from './components/infoPc'
export default {
  name: 'Index',
  data () {
    return {
    }
  },
  components: {
    IndexHeaderMobile,
    IndexHeaderPc,
    IndexInfoMobile,
    IndexFooter,
    IndexInfoPc
  }
}
</script>

<style lang="stylus" scoped>
  .el-header
    height 0 !important
    padding 0
  .el-main
    padding 0
  .el-footer
    height 0 !important
    padding 0
</style>
