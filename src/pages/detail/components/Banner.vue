<template>
    <div>
        <div class="banner">
            <img class="banner-img" @click="handleBannerClick" :src="bannerImg" alt="">
            <div class="shade">
                <div class="banner-info">
                    <div class="banner-title">{{this.sightName}}</div>
                    <div class="banner-number">
                        <span class="iconfont banner-icon">&#xe736;</span>
                        {{this.bannerImgs.length}}
                    </div>
                </div>
            </div>
        </div>
        <fade-animation>
          <common-gallary :imgs="imgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
        </fade-animation>
    </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallary: false,
      imgs: ['http://img1.qunarzz.com/sight/p0/1502/15/15ca1d0eab6bf46c.water.jpg_350x240_89202ae6.jpg', 'http://img1.qunarzz.com/sight/p0/1502/27/27d3ac6674d69424.water.jpg_350x240_95c8c915.jpg']
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  }
}
</script>

<style lang="stylus" scoped>
.banner
 height: 0
 padding-bottom: 55%
 position: relative
 overflow: hidden
 .banner-img
  width: 100%
 .shade
  right: 0
  bottom: 0
  left: 0
  height: .5rem
  position: absolute
  background-image: linear-gradient(top, rgba(0,0,0,0), rgba(0,0,0,.8))
  .banner-info
   position: absolute
   display: flex
   left: .1rem
   bottom: .2rem
   right: .1rem
   line-height: .6rem
   color: #fff
   .banner-title
    flex: 1
    font-size: .4rem
    padding: 0 .2rem
    text-shadow: .05rem .05rem .03rem #333
   .banner-number
    margin-top: .1rem
    padding: 0 .4rem
    height: .32rem
    line-height: .32rem
    border-radius: .2rem
    background: rgba(0,0,0,.8)
    font-size: .24rem
    .banner-icon
     font-size: .24rem
</style>
