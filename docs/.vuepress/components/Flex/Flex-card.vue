<template>
  <Layout-Layout
    :background-color="bgColor"
    class="flex-card"
  >
    <header class="header"></header>
    <article class="article">
      <div class="article__item">1</div>
      <div class="article__item">2</div>
      <div class="article__item">3</div>
      <div class="article__item">4</div>
      <div class="article__item">5</div>
      <div class="article__item">6</div>
    </article>
    <footer class="footer"></footer>
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
.flex-card
  display flex
  flex-flow column nowrap
  .header
    flex-basis 80px
    background-color #4E51D8
  .footer
    flex-basis 50px
    background-color #00B060
  .article
    flex auto 
    background-color #FF9000
    display flex
    flex-flow row wrap
    align-content center
    justify-content space-around
    &__item
      width 28%
      height 50px
      box-shadow 0 2px 4px rgba(255, 255, 255, .4), 3px 0 5px rgba(0, 0, 0, .6)
</style>
