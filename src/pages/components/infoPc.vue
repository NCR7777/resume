<template>
  <div class="hidden-xs-only info-PC">
    <div id="picture" class="picture" :style="{height: screenHeight + 'px'}">
      <div class="title">
        期望岗位
        <span class="job">web前端开发工程师</span>
        <span class="desc">喜欢技术 热爱挑战</span>
        <div class="scroll-button" @click="scrollToNext">
          <div class="wrapper">
            <span class="iconfont scroll-icon">&#xe679;</span>
          </div>
        </div>
      </div>
    </div>
    <div id="next" class="content" :style="{height: screenHeight + 'px'}">
      <div class="wrapper">
        <el-row class="my-info">
          <el-col :span="24" class="info-title">基本资料</el-col>
          <el-col :span="2" class="my-info-item" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">
            <div>
              <span :class="['iconfont',myInfoList[0].icon]"></span>
              <span>{{myInfoList[0].title}}</span>
              <span>{{myInfoList[0].desc}}</span>
            </div>
          </el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">dfasdfadsf</el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">dfasdfadsf</el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">dfasdfadsf</el-col>
          <el-col :span="2" class="my-info-item" :style="{height: infoItemHeight}">&nbsp;</el-col>
        </el-row>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexInfoPc',
  data () {
    return {
      infoItemHeight: '',
      screenHeight: document.documentElement.clientHeight,
      screenWidth: document.documentElement.clientWidth,
      timer: false,
      timerWidth: false,
      myInfoList: [{
        icon: 'iconicon_User',
        title: '个人信息',
        desc: '那纯瑞 | 男 | 1999年1月19日\n' +
          '西安电子科技大学 | 电子商务 | 本科应届'
      }, {
        icon: '',
        title: '',
        desc: ''
      }, {
        icon: '',
        title: '',
        desc: ''
      }, {
        icon: '',
        title: '',
        desc: ''
      }]
    }
  },
  methods: {
    scrollToNext () {
      let element = document.getElementById('next')
      element.scrollIntoView({
        block: 'end',
        behavior: 'smooth'
      })
    },
    changeHeight () {
      if (this.screenWidth > 1184) {
        this.infoItemHeight = '90%'
      } else {
        this.infoItemHeight = '45%'
      }
    }
  },
  created () {
    this.changeHeight()
  },
  mounted () {
    const that = this
    window.onresize = () => {
      return (() => {
        window.screenHeight = document.documentElement.clientHeight
        window.screenWidth = document.documentElement.clientWidth
        that.screenHeight = window.screenHeight
        that.screenWidth = window.screenWidth
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
    },
    screenWidth (val) {
      if (!this.timerWidth) {
        this.screenWidth = val
        this.changeHeight()
        this.timerWidth = true
        let that = this
        setTimeout(function () {
          that.timerWidth = false
        }, 200)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  .info-PC
    overflow hidden
    .content
      background linear-gradient(to bottom,#777,$bgColor)
      padding 0 30px
      .wrapper
        height 80%
        width 80%
        position relative
        top 50%
        left 50%
        transform translate(-50%, -50%)
        .my-info
          height 100%
          width 100%
          .info-title
            height 10%
            text-align center
            font-size 30px
            color $pcFontColor
            font-weight bolder
          .my-info-item
            border 1px solid #000
            background #25a4bb
    .picture
      background url("/static/images/intro-bg.jpg") no-repeat bottom center
      background-size cover
      .title
        width 95%
        height 45px
        text-align center
        position relative
        top 50%
        left 50%
        transform translate(-50%, -250%)
        font-size 40px
        font-weight bolder
        color #fff
        .job
          width 100%
          position absolute
          top 70px
          left 50%
          transform translateX(-50%)
          font-size 75px
          color $pcFontColor
        .desc
          width 100%
          position absolute
          top 170px
          left 50%
          transform translateX(-50%)
          font-size 25px
          font-weight normal
          letter-spacing 15px
        .scroll-button
          width 70px
          height 70px
          position absolute
          top 215px
          left 50%
          transform translateX(-60%)
          background rgba(0,0,0,.4)
          border-radius 35px
          transition all .3s
          .wrapper
            width 100%
            height 100%
            position relative
            .scroll-icon
              position absolute
              top 50%
              left 50%
              transform translate(-48%, -45%)
              font-size 30px
              transition all .3s
        .scroll-button:hover
          width 80px
          height 80px
          position absolute
          top 210px
          left 50%
          transform translateX(-60%)
          border 1px solid $pcFontColor
          border-radius 40px
          .wrapper
            width 100%
            height 100%
            position relative
            .scroll-icon
              color $pcFontColor
              font-size 35px
</style>
