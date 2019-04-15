<template>
  <div class="triangle-code">
    <pre class="code">
    {{copyCode}}
    </pre>
  </div>
</template>

<script>
export default {
  name: 'triangle-code',
  props: {
    code: {
      type: String,
      required: true
    }
  },
  watch: {
    code: {
      handler: function(code) {
        this.handleCode(code);
      },
      immediate: true
    }
  },
  data: () => {
    return {
      copyCode: ''
    }
  },
  methods: {
    handleCode(code) {
      code = code.replace(/\;/g,";\n");
      this.copyCode = `width: 0;\n height: 0;\n border: solid transparent;\n ${code}`;
    }
  }
}
</script>

<style lang="stylus" scoped>
.triangle-code
  font-family sans-serif
  box-sizing border-box
  width 100%
  height 100%
  display flex
  align-items center
  justify-content center
  padding 0 20px 4px

.code
  box-sizing border-box
  width 100%
  height 90%
  margin 0
  padding 4px 8px
  color #ffffff
  text-indent -.2rem
  white-space pre-wrap
  word-wrap break-word

</style>
