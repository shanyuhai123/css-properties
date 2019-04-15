<template>
  <div class="color-picker">
    <label for="color-picker">
      <span class="color-name" :style="{backgroundColor: color}"> {{color}} </span>
      <input type="color" v-model="color" id="color-picker" @change="changeColor">
    </label>
  </div>
</template>

<script>
export default {
  name: 'color-picker',
  data: () => {
    return {
      color: '#000000'
    }
  },
  mounted() {
    this.changeColor();
  },
  methods: {
    changeColor() {
      this.$emit('getColor', this.color);
    }
  }
}
</script>


<style lang="stylus" scoped>
.color-picker
  width 100%
  height 100%
  display flex
  align-items center
  justify-content center

#color-picker
  width 0
  height 0
  opacity 0
  filter opacity(0)
  display none

.color-name
  background-color red
  color #ffffff
  padding 6px 8px
</style>
