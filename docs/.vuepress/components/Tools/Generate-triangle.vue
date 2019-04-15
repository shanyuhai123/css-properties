<template>
  <Layout-Layout
    :background-color="bgColor"
    class="generate-triangle"
  >
    <aside class="settings">
      <section class="settings_direction">
        <h4 class="title">三角形方向</h4>
        <Tools-Triangle-direction @getDirection="getDirection"></Tools-Triangle-direction>
      </section>
      <section class="settings_type">
        <h4 class="title">三角形类型</h4>
        <Tools-Triangle-type :type="direction" v-if="direction" @getType="getType"></Tools-Triangle-type>
        <Tools-Triangle-width v-if="type" :type="type" :direction="direction" @getBorderWidth="getBorderWidth"></Tools-Triangle-width>
      </section>
      <section class="settings_color">
        <h4 class="title">三角形颜色</h4>
        <Tools-Color-picker @getColor="getColor"></Tools-Color-picker>
      </section>
    </aside>
    <main class="exhibition">
      <section class="rendering">
        <h4 class="title">效果图</h4>
        <Tools-Triangle-paint :color="color" :direction="direction" :borderWidth="borderWidth" v-if="direction" @getCode="getCode"></Tools-Triangle-paint>
      </section>
      <section class="code">
        <h4 class="title">代码</h4>
        <Tools-Triangle-code v-if="code" :code="code"></Tools-Triangle-code>
      </section>
    </main>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#c0c4c3", // 月影白
      direction: '',
      type: '',
      color: '',
      borderWidth: '',
      code: ''
    };
  },
  methods: {
    getDirection(direction) {
      this.direction = direction;
    },
    getType(type) {
      this.type = type;
    },
    getColor(color) {
      this.color = color;
    },
    getBorderWidth(borderWidth) {
      this.borderWidth = borderWidth;
    },
    getCode(code) {
      this.code = code;
    }
  }
};
</script>

<style lang="stylus" scoped>
.generate-triangle
  display flex
  .title
    margin 0
    padding 0
  .settings
    flex-basis 30%
  .exhibition
    flex auto
    background-color #cdd1d3 // 银鱼白

.settings
  display flex
  flex-direction column
  padding-top 8px
  .settings_direction,
  .settings_type,
  .settings_color
    display flex
    flex-direction column
    align-items center
  .settings_type,
  .settings_color
    flex-basis 22%
  .settings_direction
    flex auto

.exhibition
  display flex
  flex-direction column
  padding-top 8px
  .rendering,
  .code
    display flex
    flex-direction column
    align-items center
  .code
    flex-basis 38%
  .rendering
    flex auto

</style>
