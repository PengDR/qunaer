<template>
    <div>
      <div class="title">周末去哪儿</div>
      <ul>
          <li class="item border-bottom" v-for="item of weekendLists" :key="item.id">
              <div class="item-img-wrapper">
                  <img class="item-img" :src="item.imgUrl">
              </div>
              <div class="item-info">
                  <p class="item-title">{{item.title}}</p>
                  <p class="item-desc">{{item.desc}}</p>
              </div>
          </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekendLists: Array
  }
}

</script>

<style lang="stylus" scoped>
    @import '~styles/mixins.styl'
    .title
     line-height: .8rem
     background: #eeeeee
     text-indent: .2rem
    .item-img-wrapper
     overflow: hidden
     height: 0
     padding-bottom: 37.09%
     .item-img
      width: 100%
    .item-info
     flex: 1
     padding: .14rem .2rem .2rem .2rem
     .item-title
      line-height: .54rem
      font-size: .3rem
      ellipsis()
     .item-desc
      line-height: .4rem
      color: #616161
      font-size: .2rem
      ellipsis()
</style>
