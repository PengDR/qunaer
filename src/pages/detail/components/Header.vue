<template>
    <div>
        <div class="header-abs" v-show="showAbs">
            <router-link tag="div" to="/" class="iconfont header-abs-back">&#xe624;</router-link>
        </div>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            <router-link to="/">
            <div class="iconfont header-back-fixed">&#xe624;</div>
            </router-link>
            景点详情
        </div>
    </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 1) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  mounted () { /* 页面展示执行 */
    window.addEventListener('scroll', this.handleScroll)
  },
  unmounted () { /* 页面切换时执行 */
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header-abs
 position: absolute
 text-align: center
 left: .2rem
 top: .2rem
 width: .8rem
 height: .8rem
 line-height: .8rem
 border-radius: .4rem
 background: rgba(0,0,0,.8)
 .header-abs-back
  color: #ffffff
  font-size: .4rem
.header-fixed
 z-index: 10
 position: fixed
 top: 0
 left: 0
 right: 0
 height: .86rem
 line-height: .86rem
 text-align: center
 color: #ffffff
 background: $bgColor
 font-size: .32rem
 .header-back-fixed
   position: absolute
   top: 0
   left: 0
   width: .64rem
   text-align: center
   font-size: .4rem
   color: #fff
</style>
