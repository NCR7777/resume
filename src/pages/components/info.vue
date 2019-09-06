<template>
  <div>
    <div class="about-me" :style="{height: screenHeight+'px'}">
        <div class="my-photo animated zoomIn">
          <div class="photo"></div>
        </div>
      <div class="name animated heartBeat">那纯瑞</div>
    </div>
    <div class="info2" :style="{height: screenHeight+'px'}">
    </div>
    <div class="info3" :style="{height: screenHeight+'px'}">
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexInfo',
  data () {
    return {
      screenHeight: document.documentElement.clientHeight - 50,
      timer: false
    }
  },
  mounted () {
    const that = this
    window.onresize = () => {
      return (() => {
        window.screenHeight = document.documentElement.clientHeight - 50
        that.screenHeight = window.screenHeight
      })()
    }
  },
  watch: {
    screenHeight (val) {
      if (!this.timer) {
        this.screenHeight = val
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
  .about-me
    padding-top 5%
    .my-photo
      width 3rem
      height 3rem
      margin 0 auto
      background #fff
      overflow hidden
      border-radius 1.5rem
      box-shadow 0 0 .5rem #333333
      .photo
        width 100%
        height 100%
        background url("/static/images/my-photo.jpg") no-repeat .15rem .05rem
        background-size 90% 90*1.453%
    .name
      display block
      width 3.5rem
      line-height 1rem
      text-align center
      font-size .5rem
      margin .3rem auto
      background burlywood
      color black
      border-radius .5rem
      box-shadow 0 0 .1rem #333333 inset

  .info2
    background black

  .info3
    background blueviolet
    height 50rem
</style>
