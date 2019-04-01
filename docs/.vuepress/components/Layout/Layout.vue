<template>
  <div :class="['layout', {'align-center': alignCenter, 'justify-center': justifyCenter}]" :style="{backgroundColor: backgroundColor}">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    alignCenter: {
      type: Boolean,
      default: false
    },
    justifyCenter: {
      type: Boolean,
      default: false
    },
    backgroundColor: {
      type: String
    }
  }
}
</script>


<style lang="stylus" scoped>
.layout
  width 100%
  height 100%
  min-height 468px
  margin 0!important
  box-sizing border-box
  overflow hidden

.align-center
  display flex
  align-items center

.justify-center
  display flex
  justify-content center
</style>

