<template>
  <Layout-Layout
    align-center
    justify-center
    :background-color="bgColor"
  >
    <div class="flex__item">大哥</div>
    <div class="flex__item">二弟</div>
    <div class="flex__item">三妹</div>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#c0c4c3", // 月影白
    };
  }
};
</script>

<style lang="stylus" scoped>
.flex__item
  width 15%
  height 15%
  box-shadow 0 0 4px rgba(0, 0, 0, .5), inset 2px 0 1px rgba(0, 0, 0, .2)
  display flex
  align-items center
  justify-content center
  cursor pointer
  user-select none
  color #142334 // 钢青
  &:nth-child(1)
    width 20%
    height 20%
    &::after
      position absolute
      content 'flex-end'
      padding 10px 6px
      border-radius 6px
      color #e0c8d1 // 淡青紫
      background-color #1661ab // 靛青
      transition all 0.5s linear
      opacity 0
    &:active
      transition all .5s linear 
      align-self flex-end
  &:nth-child(2)
    width 16%
    height 18%
    &::before
      position absolute
      content 'flex_start'
      padding 10px 6px
      border-radius 6px
      color #e0c8d1 // 淡青紫
      background-color #1661ab // 靛青
      transition all 0.5s linear
      opacity 0
    &:active
      align-self flex-start
  &:nth-child(3)
    width 14%
    height 28%
    &::before
      position absolute
      content 'flex_start'
      padding 10px 6px
      border-radius 6px
      color #e0c8d1 // 淡青紫
      background-color #1661ab // 靛青
      transition all 0.5s linear
      opacity 0
    &:active
      align-self flex-start


.flex__item:hover::before
  transform translateY(80px)
  opacity 1
.flex__item:hover::after
  transform translateY(-80px)
  opacity 1

.flex__item:active::before,
.flex__item:active::after
  color #f1908c // 榴子红
  background-color #fff
  box-shadow 0 2px 4px rgba(0, 0, 0, .5), 2px 0 4px rgba(0, 0, 0, .6)

</style>
