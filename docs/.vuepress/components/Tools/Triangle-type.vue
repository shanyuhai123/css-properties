<template>
  <div class="triangle-type">
    <button
      class="type-button"
      v-for="(type, index) in triangleTypes"
      v-show="type.en !== 'equilateral' || equilateral"
      :key="index"
      :class="{active: index === active}"
      @click.stop="changeType(type.en, index)"
    >{{type.zh}}</button>
  </div>
</template>

<script>
export default {
  name: "triangle-type",
  data: () => {
    return {
      active: 0,
      equilateral: false,
      triangleTypes: [
        {
          en: "equilateral",   
          zh: "等边"
        },
        {
          en: "isosceles",
          zh: "等腰"
        },
        {
          en: "scalene",
          zh: "不等边"
        }
      ]
    };
  },
  props: {
    type: {
      type: String,
      validator: function(val) {
        return [
          "top",
          "right",
          "left",
          "bottom",
          "top-left",
          "top-right",
          "bottom-left",
          "bottom-right"
        ].includes(val);
      }
    }
  },
  watch: {
    type: {
      handler: function(val) {
        const isPositive = ["top", "right", "left", "bottom"].includes(val);
        this.equilateral = isPositive;
        if (isPositive) {
          this.changeType('equilateral', 0);     
        } else {
          this.changeType('isosceles', 1);
        }
      },
      immediate: true
    }
  },
  methods: {
    changeType(item, index) {
      this.active = index;
      this.$emit("getType", item);
    }
  }
};
</script>

<style lang="stylus" scoped>
.triangle-type
  width 100%
  height 100%
  display flex
  align-items center
  justify-content space-around

.type-button
  outline none
  border none 
  padding 4px 6px
  cursor pointer

.active
  background-color #3b818c // 蜻蜓蓝
  color #ffffff
</style>
