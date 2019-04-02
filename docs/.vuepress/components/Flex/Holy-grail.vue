<template>
  <Layout-Layout
    :background-color="bgColor"
    class="holy-grail"
  >
    <div class="flex__content">content</div>
    <div class="flex__nav">nav</div>
    <div class="flex__side">side</div>
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
.holy-grail
  display flex
  .flex__content
    flex 1 1 auto
    background-color #009999
  .flex__nav, .flex__side
    flex 0 0 120px
  .flex__nav
    order -1
    background-color #1D7373
  .flex__side
    background-color #33CCCC
  
</style>