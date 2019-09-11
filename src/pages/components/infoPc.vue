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
            <div class="info-item">
              <span :class="['iconfont',myInfoList[0].icon,'info-icon']"></span>
              <span class="info-title">{{myInfoList[0].title}}</span>
              <span class="info-desc" v-html="myInfoList[0].desc">{{myInfoList[0].desc}}</span>
            </div>
          </el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">
            <div class="info-item">
              <span :class="['iconfont',myInfoList[1].icon,'info-icon']"></span>
              <span class="info-title">{{myInfoList[1].title}}</span>
              <span class="info-desc" v-html="myInfoList[1].desc">{{myInfoList[1].desc}}</span>
            </div>
          </el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">
            <div class="info-item">
              <span :class="['iconfont',myInfoList[2].icon,'info-icon']"></span>
              <span class="info-title">{{myInfoList[2].title}}</span>
              <span class="info-desc" v-html="myInfoList[2].desc">{{myInfoList[2].desc}}</span>
            </div>
          </el-col>
          <el-col :span="2" class="my-info-item hidden-lg-and-up" :style="{height: infoItemHeight}">&nbsp;</el-col>
          <el-col :sm="9" :md="9" :lg="5" :xl="5" class="my-info-item" :style="{height: infoItemHeight}">
            <div class="info-item">
              <span :class="['iconfont',myInfoList[3].icon,'info-icon']"></span>
              <span class="info-title">{{myInfoList[3].title}}</span>
              <span class="info-desc" v-html="myInfoList[3].desc">{{myInfoList[3].desc}}</span>
            </div>
          </el-col>
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
        desc: '<br>那纯瑞 | 男<br>1999年1月19日<br>西安电子科技大学<br>电子商务 | 本科应届'
      }, {
        icon: 'iconicon_Call',
        title: '联系方式',
        desc: '<br>电话<br>186-294-88674<br>邮箱<br><a href="mailto: ncr0119@163.com">ncr0119@163.com</a>'
      }, {
        icon: 'icongithub',
        title: '个人网站',
        desc: '<br>Github<br><a href="https://github.com/NCR7777" target="_blank">github.com/NCR7777</a><br>个人博客(无文章)<br><a href="http://www.ncrlhym.cn" target="_blank">www.ncrlhym.cn</a>'
      }, {
        icon: 'iconai-code',
        title: '程序人生',
        desc: '<br>HTML/CSS/JS: 5000+行<br>Vue: 1000+行<br>Node.Js: 1500+行<br>Java/JSP: 2000+行'
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
      this.screenWidth = val
      this.changeHeight()
      console.log(this.screenWidth)
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
      min-height 750px
      .wrapper
        height 80%
        width 90%
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
            text-align center
            position relative
            .info-item
              overflow hidden
              position absolute
              top 50%
              left 50%
              transform translate(-50%, -50%)
              .info-icon
                margin 0 25px
                display block
                font-size 130px
                color #aaa
                transition color .5s
              .info-title
                margin-top 10px
                display block
                font-size 25px
              .info-desc
                margin-top 5px
                display block
                font-size 12px
                font-weight normal
                line-height 18px
                letter-spacing 1px
                color #ccc
                transition all .5s
              .info-desc:hover
                font-size 14px
                font-weight bolder
                color $pcFontColor
              .info-icon:hover
                color $pcFontColor
    .picture
      background url("/static/images/intro-bg.jpg") no-repeat bottom center
      background-size cover
      min-height 350px
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
