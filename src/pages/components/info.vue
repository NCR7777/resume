<template>
  <div>
    <div :class="photoClass">
        <div class="my-photo animated zoomIn">
          <div class="photo"></div>
        </div>
      <div class="name animated heartBeat">{{myName}}</div>
      <div class="info animated zoomIn" v-for="(item, index) of aboutMe" :key="index">
        <div class="info-title border-bottom">
          <div class="left-mark"></div>
          <div class="info-title-desc">{{item.myInfo}}</div>
        </div>
        <ul class="item">
            <li class="item-desc" v-for="(itemChild, index) of item.children" :key="index">
              <div class="icon-svg" v-if="itemChild.iconSvg">
                <swiper :options="swiperOption">
                  <swiper-slide v-for="(page, index) of pages" :key="index">
                    <div class="icon-svg-item" v-for="(itemChildIcon, index) of page" :key="index">
                      <div class="icon-svg-item-iconName"
                            v-html="itemChildIcon.iconName">{{itemChildIcon.iconName}}</div>
                      <div class="icon-svg-item-skillDesc">{{itemChildIcon.skillDesc}}</div>
                    </div>
                  </swiper-slide>
                  <div class="swiper-pagination" slot="pagination"></div>
                </swiper>
              </div>
              <span v-if="itemChild.icon" :class="['iconfont',itemChild.icon]"></span>
              <span class="item-normal-desc" v-if="itemChild.desc" v-html="itemChild.desc">{{itemChild.desc}}</span>
              <span class="item-project-desc" v-if="itemChild.projectDesc" v-html="itemChild.projectDesc">{{itemChild.projectDesc}}</span>
            </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexInfo',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: 5000,
        autoplayDisableOnInteraction: false,
        mousewheelControl: true,
        observeParents: true,
        loop: true
      },
      myName: '那纯瑞',
      screenHeight: document.documentElement.clientHeight - 50,
      timer: false,
      photoClass: 'about-me-new',
      aboutMe: [{
        myInfo: '联系方式',
        children: [{
          icon: 'iconicon_Call',
          desc: '电话 18629488674 | 18845155191'
        }, {
          icon: 'iconicon_Email',
          desc: '邮箱 <a href="mailto: ncr0119@163.com">ncr0119@163.com</a>'
        }]
      }, {
        myInfo: '个人信息',
        children: [{
          icon: 'iconicon_User',
          desc: '那纯瑞 | 男 | 1999年1月19日'
        }, {
          icon: 'iconicon_Read',
          desc: '西安电子科技大学 | 电子商务 | 本科应届'
        }, {
          icon: 'iconicon_Folder',
          desc: '期望职位:<span style="color: red">web前端开发工程师(深圳)</span>'
        }, {
          icon: 'icongithub',
          desc: '我的Github:<a href="https://github.com/NCR7777" target="_blank">https://github.com/NCR7777</a>'
        }, {
          icon: 'iconblogger',
          desc: '我的博客:<a href="http://www.ncrlhym.cn" target="_blank">http://www.ncrlhym.cn</a>'
        }]
      }, {
        myInfo: '技能掌握',
        children: [{
          iconSvg: [{
            iconName: '<svg class="icon" aria-hidden="true">' +
                '  <use xlink:href="#iconVue"></use>' +
              '</svg>',
            skillDesc: 'Vue'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconHTML"></use>' +
              '</svg>',
            skillDesc: 'HTML5'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconCSS"></use>' +
              '</svg>',
            skillDesc: 'CSS3'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconJavaScript"></use>' +
              '</svg>',
            skillDesc: 'JavaScript'
          }, {
            iconName: '<img src="/static/images/es6.jpg" alt="ES6" style="width: .8rem">',
            skillDesc: 'ES6'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#icongit"></use>' +
              '</svg>',
            skillDesc: 'Git'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#icongitlab"></use>' +
              '</svg>',
            skillDesc: 'GitLab'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconjQuery"></use>' +
              '</svg>',
            skillDesc: 'jQuery'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconMySQL"></use>' +
              '</svg>',
            skillDesc: 'MySQL'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconNodejs"></use>' +
              '</svg>',
            skillDesc: 'Nodejs'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconBootstrap"></use>' +
              '</svg>',
            skillDesc: 'Bootstrap'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconAdobe-Photoshop"></use>' +
              '</svg>',
            skillDesc: 'PhotoShop'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconwebstorm"></use>' +
              '</svg>',
            skillDesc: 'WebStorm'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconAdobe-Dreamweaver"></use>' +
              '</svg>',
            skillDesc: 'Dreamweaver'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconMicrosoft-Word"></use>' +
              '</svg>',
            skillDesc: 'Word'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconMicrosoft-Powerpoint"></use>' +
              '</svg>',
            skillDesc: 'Powerpoint'
          }, {
            iconName: '<svg class="icon" aria-hidden="true">' +
              '  <use xlink:href="#iconMicrosoft-Excel"></use>' +
              '</svg>',
            skillDesc: 'Excel'
          }]
        }]
      }, {
        myInfo: '项目作品',
        children: [{
          icon: 'iconicon_Favorite',
          projectDesc: '个人博客:<a href="http://www.ncrlhym.cn" target="_blank">那纯瑞的博客</a><br/>' +
            'Node.JS+Express框架+mysql数据库等<br/>' +
            '登陆注册，整合富文本编辑器、文章展示，评论管理等' +
            ''
        }, {
          icon: 'iconicon_Favorite',
          projectDesc: '仿去哪网:<a href="https://ncr7777.github.io/qunar/index.html" target="_blank">仿去哪网</a> <span style="color: red">(网速较慢)</span><br/>' +
            'Vue,Vuex,Vue-Router,Axios,swiper,stylus等<br/>' +
            '取消默认样式、适配移动端，路由配置，组件化开发，轮播效果，图标分页，组件间传值，keep-alive滚动事件，全局事件解绑等'
        }, {
          icon: 'iconicon_Favorite',
          projectDesc: '页面特效:<a href="https://ncr7777.github.io/pages.html" target="_blank">请使用电脑访问</a> <span style="color: red">(部分不适配手机)</span><br/>' +
            'html,css等<br/>' +
            'css3动画，flex布局，box-shadow阴影等'
        }, {
          icon: 'iconicon_Favorite',
          projectDesc: '二次开发ecshop:<a href="https://www.kuailehaigou.com" target="_blank">拾贝E购</a> <span style="color: red">(请勿下单)</span><br/>' +
            'PHP+阿里云Ecs+宝塔面板等<br/>' +
            '修复商家入驻页面跳转bug，按照需求删除无用信息以及部分内容的修改，域名备案，SSL证书布置等'
        }, {
          icon: 'iconicon_Favorite',
          projectDesc: '电影网站首页:<a href="http://www.hawgreencar.club" target="_blank">Movie</a> <span style="color: red">(仅一个页面)</span><br/>' +
            'html,css,js,jquery等<br/>' +
            '轮播图，css3动画等'
        }]
      }]
    }
  },
  methods: {
    calculateHeight () {
      if (this.screenHeight <= 640) {
        this.photoClass = 'about-me-old'
      } else {
        this.photoClass = 'about-me-new'
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.aboutMe[2].children[0].iconSvg.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  },
  mounted () {
    this.calculateHeight()
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
  @import "~style/mixins.styl"
  .my-photo >>>
  .photo
    width 100%
    height 100%
    background url("/static/images/my-photo.jpg") no-repeat .15rem .05rem
    background-size 90% 90*1.453%
  .info
    width 100%
  .info-title
    display flex
    width 100%
    height .6rem
    margin .2rem 0
  .left-mark
    width .15rem
    height .6rem
    background tomato
  .info-title-desc
    padding-left .2rem
    line-height .6rem
    font-size .36rem
    font-weight bolder
    ellipsis()
  .item
    line-height .45rem
    padding 0 .4rem
    font-size .28rem
  .item-desc
    display flex
    padding .1rem .1rem
    margin  .15rem .1rem
    background #f5f5f5
    border-radius .1rem
  .item-normal-desc
    padding-left .2rem
    ellipsis()
  .item-project-desc
    padding-left .2rem
  .item-desc-info
    color black
  .swiper-container
    height 0
    padding-bottom 54%
  .swiper-pagination
    position absolute
    bottom -.1rem
  .icon-svg
    width 100%
  .icon-svg-item
    overflow hidden
    float left
    width 25%
    height 0
    padding-bottom 25%
  .icon-svg-item-iconName
    margin-top .15rem
    font-size 2.8em
    text-align center
  .icon-svg-item-skillDesc
    text-align center
    ellipsis()
  .about-me-new
    padding-top 3%
    overflow hidden
    .my-photo
      width 3rem
      height 3rem
      margin 0 auto
      background #fff
      overflow hidden
      border-radius 1.5rem
      box-shadow 0 0 .22rem #333333
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
  .about-me-old
    padding-top 3%
    overflow hidden
    .my-photo
      width 2rem
      height 2rem
      margin 0 auto
      background #fff
      overflow hidden
      border-radius 1rem
      box-shadow 0 0 .22rem #333333
    .name
      display block
      width 2.5rem
      line-height .8rem
      text-align center
      font-size .35rem
      margin .3rem auto
      background burlywood
      color black
      border-radius .5rem
      box-shadow 0 0 .1rem #333333 inset
</style>
