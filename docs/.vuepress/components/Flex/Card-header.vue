<template>
  <Layout-Layout
    align-center
    justify-center
    :background-color="bgColor"
  >
    <header class="header">
      <div class="header__avatar"></div>
      <div class="header__title">Title</div>
      <div class="header__more"></div>
    </header>
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
.header
  height 100px
  width 100%
  background-color #f9f1db // 蚌肉白
  display flex
  align-items center
  > *
    margin 0 10px
  &__avatar, &__more
    flex 0 0 80px
    height 80px
    border-radius 50%
  &__avatar
    background-color #FFAC40
  &__title
    color #FF9000
  &__more
    margin-left auto
    background-color #A65E00

</style>
