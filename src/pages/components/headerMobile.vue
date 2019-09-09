<template>
  <div class="hidden-sm-and-up top">
    <div class="header" v-show="showHeader" :style="opacityStyle">
      <span class="title">那纯瑞 | <span class="small">西安电子科技大学</span></span>
      <i :class="['el-icon-s-operation','menu',menuIconColorClass]" @click="handleShowMenu"></i>
    </div>
    <div  class="menu-list" :style="opacityStyle">
      <transition enter-active-class="animated bounceInDown" leave-active-class="animated bounceOutUp">
        <menu-mobile v-show="clickShowMenu && showMenu" v-click-out-side="handleCloseMenu"></menu-mobile>
      </transition>
    </div>
  </div>
</template>

<script>
import MenuMobile from './menuMobile'
export default {
  name: 'IndexHeaderMobile',
  data () {
    return {
      showHeader: false,
      showMenu: false,
      clickShowMenu: false,
      num: 0,
      menuIconColorClass: 'white',
      opacityStyle: {
        opacity: 0
      }
    }
  },
  components: {
    MenuMobile
  },
  methods: {
    handleShowMenu () {
      if (!this.showMenu) {
        this.num = 1
      }
      this.showMenu = !this.showMenu
      this.menuIconColorClass = this.clickShowMenu && this.showMenu ? 'blue' : 'white'
    },
    handleCloseMenu () {
      if (this.num === 1) {
        this.clickShowMenu = true
      } else {
        this.showMenu = false
        this.clickShowMenu = false
      }
      this.num = 0
      this.menuIconColorClass = this.clickShowMenu && this.showMenu ? 'blue' : 'white'
    },
    handleScroll () {
      const scrollTop = document.documentElement.scrollTop
      let opacity = 0
      if (scrollTop > 100) {
        this.showHeader = true
        opacity = opacity < 1 ? (scrollTop - 100) / 200 : 1
      } else {
        this.showHeader = false
      }
      this.opacityStyle = { opacity }
    }
  },
  directives: {
    clickOutSide: {
      bind: function (el, binding, vnode) {
        function documentHandler (e) {
          if (el.contains(e.target)) {
            return false
          }
          if (binding.expression) {
            binding.value(e)
          }
        }
        el._vueClickOutSide_ = documentHandler
        document.addEventListener('click', el._vueClickOutSide_)
      },
      unbind: function (el, binding) {
        document.removeEventListener('click', el._vueClickOutSide_)
        delete el._vueClickOutSide_
      }
    }
  },
  activated () {
    this.showHeader = false
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/mixins.styl"
  @import "~style/variables.styl"
  .top
    position fixed
    width 100%
    z-index 4
    .header
      width 100%
      height 0
      padding-bottom 1rem
      line-height 1rem
      font-size .32rem
      color #fff
      background $bgColor
      z-index 3
      .title
        display block
        width: 65%;
        padding 0 .4rem
        ellipsis()
        .small
          font-size .26rem
      .menu
        position absolute
        top 0
        right .4rem
        line-height 1rem
        font-size .5rem
        transition color 1.5s
      .white
        color #fff
      .blue
        color #66b1ff
      .bounceInUP
        width 100%
        position fixed
        top 1rem
      .bounceOutDown
        width 100%
        position absolute
        top 1rem
    .menu-list
      z-index 2
</style>
