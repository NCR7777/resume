<template>
  <div>
    <div class="hidden-sm-and-up footer-mobile">© 那纯瑞 | 西安电子科技大学</div>
    <div class="hidden-xs-only footer-PC">© 那纯瑞 | 西安电子科技大学</div>
  </div>
</template>

<script>
export default {
  name: 'IndexFooter'
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  .footer-mobile
    color white
    line-height .5rem
    background $bgColor
    text-align center
  .footer-PC
    color white
    line-height 50px
    background $bgColor
    text-align center
</style>
