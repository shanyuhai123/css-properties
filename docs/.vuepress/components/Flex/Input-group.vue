<template>
  <Layout-Layout
    align-center
    justify-center
    :background-color="bgColor"
  >
    <div class="input-group">
      <span class="title" @click="message = !message" v-if="message">Message</span>
      <input type="text" class="input-text">
      <span class="icon"  @click="icon = !icon" v-if="icon"></span>
    </div>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#c0c4c3", // 月影白
      message: true,
      icon: true
    };
  }
};
</script>

<style lang="stylus" scoped>
.input-group
  flex 0 0 75%
  height 40px
  border 2px solid #3c9566 // 蟾绿
  border-radius 4px
  display flex
  align-items center
  > *
    box-sizing border-box
  .input-text
    font-size 20px
    padding-left 10px
    height 100%
    flex auto
    outline none 
    border none 
  .icon
    flex 0 0 24px
    width 24px
    height 24px
    border-radius 50%
    background-color #648e93 // 晚波蓝
</style>
