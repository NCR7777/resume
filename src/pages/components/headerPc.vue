<template>
    <div class="hidden-xs-only header" :style="{
    background: headerBg, lineHeight: headerHeight}">
      <el-row>
        <el-col :sm="1" :md="3" :lg="4" :xl="4">&nbsp;</el-col>
        <el-col :sm="22" :md="18" :lg="16" :xl="16">
          <span class="title"><span class="name"><b>那纯瑞</b></span> | 西安电子科技大学</span>
          <div class="menu">
            <span v-for="(item, index) of menuList" :key="index"><a :href="item.url" :target="item.target" class="menu-item">{{item.desc}}</a></span>
          </div>
        </el-col>
      </el-row>
    </div>
</template>

<script>
export default {
  name: 'IndexHeaderPc',
  data () {
    return {
      screenHeight: document.documentElement.clientHeight,
      headerBg: '',
      headerHeight: '70px',
      timer: false,
      menuList: [{
        desc: '关于我',
        url: ''
      }, {
        desc: '我的Github',
        url: 'https://github.com/NCR7777',
        target: '_blank'
      }, {
        desc: '我的博客',
        url: 'http://www.ncrlhym.cn',
        target: '_blank'
      }, {
        desc: '联系我',
        url: ''
      }]
    }
  },
  methods: {
    handleScroll () {
      this.screenHeight = document.documentElement.clientHeight
      const scrollTop = document.documentElement.scrollTop
      if (scrollTop >= this.screenHeight - 50) {
        this.headerBg = '#3f424b'
        this.headerHeight = '50px'
      } else {
        this.headerBg = ''
        this.headerHeight = '70px'
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  .header
    position fixed
    width 100%
    color white
    transition all .8s
    z-index 99
    .name
      font-size .4rem
      color $pcFontColor
    .menu
      float right
      .menu-item
        margin-left 35px
        color #fff
      .menu-item:hover
        color $pcFontColor
</style>
