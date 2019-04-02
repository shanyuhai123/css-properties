<template>
  <Layout-Layout
    :background-color="bgColor"
    class="flex-layout"
  >
    <div class="flex__item">left</div>
    <div class="flex__item">right</div>
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
.flex-layout
  display flex
.flex__item
  &:nth-child(1)
    background-color #c04851 // 玉红
    flex 0 0 200px
  &:nth-child(2)
    background-color #440e25 // 古铜紫
    flex 1 1 auto 
</style>
