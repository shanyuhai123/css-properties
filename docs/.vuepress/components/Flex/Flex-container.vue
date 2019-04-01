<template>
  <Layout-Layout
    :background-color="bgColor"
  >
    <div class="flex">
      <input type="checkbox" class="toggle" v-for="(checkbox, index) in checkboxs()" :id="checkbox">
      <section class="flex__feats">
        <div class="feat__list" v-for="(feat, index) in feats()" :key="index">
          <h4 class="feat__list_title">{{feat.title}}</h4>
          <div class="feat__list_labels">
            <label v-for="(item, index) in feat.list" :key="index" :for="`${feat.title}-${item}`" :class="`${feat.title}-${item}`">{{item}}</label>
          </div>
        </div>
      </section>
      <div class="divider"></div>
      <section class="flex__exh">
        <div class="exh__item" v-for="n in 3" :key="n"></div>
      </section>
    </div>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#c0c4c3", // 月影白
      feats: () => {
        return [
          {title: "jusitify", list : ["flex-start", "flex-end", "center", "space-between", "space-around"]},
          {title: "align", list : ["flex-start", "flex-end", "center"]}
        ]
      },
      checkboxs: () => {
        return [
          "jusitify-flex-start", "jusitify-flex-end", "jusitify-center", "jusitify-space-between", "jusitify-space-around", "align-flex-start", "align-flex-end", "align-center"
        ]
      }
    };
  }
};
</script>

<style lang="stylus" scoped>
.flex
  width 100%
  height 100%
  display flex
  *
    box-sizing border-box
  &__feats
    flex-basis 28%
    height 100%
    display flex
    justify-content space-around
    .feat__list
      display flex
      flex-direction column
      justify-content flex-start
      align-items center
    .feat__list_labels
      flex-grow 1
      display flex
      flex-direction column
      justify-content space-around
      align-items center  
      cursor pointer
  &__exh
    flex-grow 1
    padding 16px
    .exh__item
      width 15%
      height 15%
      box-shadow 0 0 4px rgba(0, 0, 0, .5)
      &:nth-child(1)
        width 18%
        height 20%
      &:nth-child(2)
        width 14%
        height 18%
      &:nth-child(3)
        width 15%
        height 15%


.divider
  width 1px
  height 100%
  margin 0 2px
  background-color #000;

.toggle[type="checkbox"]
  width 0
  height 0
  filter opacity(0)
  opacity 0
  display none

#jusitify-flex-start:checked ~ .flex__feats .jusitify-flex-start
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白
  
#jusitify-flex-end:checked ~ .flex__feats .jusitify-flex-end
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白
    
#jusitify-center:checked ~ .flex__feats .jusitify-center
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白
    
#jusitify-space-between:checked ~ .flex__feats .jusitify-space-between
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白
    
#jusitify-space-around:checked ~ .flex__feats .jusitify-space-around
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白
    
#align-flex-start:checked ~ .flex__feats .align-flex-start
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白
    
#align-flex-end:checked ~ .flex__feats .align-flex-end
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白

#align-center:checked ~ .flex__feats .align-center
  padding 4px 4px
  background-color #5a191b // 栗紫
  color #fffef9 // 雪白

#jusitify-flex-start:checked ~ .flex__exh
  display flex
  justify-content flex-start

#jusitify-flex-end:checked ~ .flex__exh
  display flex
  justify-content flex-end
    
#jusitify-center:checked ~ .flex__exh
  display flex
  justify-content center
    
#jusitify-space-between:checked ~ .flex__exh
  display flex
  justify-content space-between
    
#jusitify-space-around:checked ~ .flex__exh
  display flex
  justify-content space-around
    
#align-flex-start:checked ~ .flex__exh
  display flex
  align-items flex-start
    
#align-flex-end:checked ~ .flex__exh
  display flex
  align-items flex-end

#align-center:checked ~ .flex__exh
  display flex
  align-items center
</style>
