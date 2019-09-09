<template>
  <div class="hidden-xs-only info-PC">
    <div class="picture" :style="{height: screenHeight + 'px'}"></div>
  </div>
</template>

<script>
export default {
  name: 'IndexInfoPc',
  data () {
    return {
      screenHeight: document.documentElement.clientHeight
    }
  },
  mounted () {
    const that = this
    window.onresize = () => {
      return (() => {
        window.screenHeight = document.documentElement.clientHeight
        that.screenHeight = window.screenHeight
      })()
    }
  },
  watch: {
    screenHeight (val) {
      if (!this.timer) {
        this.screenHeight = val
        this.calculateHeight()
        this.timer = true
        let that = this
        setTimeout(function () {
          that.timer = false
        }, 400)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .picture
    background url("/static/images/intro-bg.jpg") no-repeat bottom center
    background-size cover
</style>
