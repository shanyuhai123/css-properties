<template>
  <div class="triangle-rendering">
    <div class="triangle" ref="triangleRendering" :style="[borderStyle, { borderWidth: borderWidth }]"></div>
  </div>
</template>

<script>
export default {
  name: 'triangle-rendering',
  props: {
    direction: {
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
    },
    color: {
      type: String,
      default: '#000000'
    },
    borderWidth: {
      type: String
    }
  },
  watch: {
    direction: {
      handler: function(direction) {
        const isPositive = ["top", "right", "left", "bottom"].includes(direction);
        if (isPositive) {
          let target = this.translate.filter(item => item.source === direction)[0].target;
          direction = target;
        }
        this.target = {};
        const style = direction.split('-');
        style.forEach(el => {
          el = this.capitalize(el);
          this.target[`border${el}Color`] = this.color;
        });
        this.borderStyle = this.target;
      },
      immediate: true
    },
    color: {
      handler: function(color) {
        let tempTarget = {};
        for (var key in this.target) {
          tempTarget[key] = color;
        }
        this.target = tempTarget;
        this.borderStyle = this.target;
      },
      immediate: true
    },
    borderStyle: {
      handler: function() {
        this.postCode();
      },
      immediate: true
    },
    borderWidth: {
      handler: function() {
        this.postCode();
      },
      immediate: true
    }
  },
  data: () => {
    return {
      borderStyle: {},
      target: {},
      translate: [
        {
          source: 'top',
          target: 'bottom'
        },
        {
          source: 'bottom',
          target: 'top'
        },
        {
          source: 'left',
          target: 'right'
        },
        {
          source: 'right',
          target: 'left'
        }
      ]
    }
  },
  methods: {
    capitalize(str) {
      return str.toLowerCase().replace(/( |^)[a-z]/g, (L) => L.toUpperCase())
    },
    postCode() {
      this.$nextTick(() => {
        let dom = this.$refs.triangleRendering;
        let code = dom.attributes.style.textContent;
        
        this.$emit('getCode', code);
      })
    }
  }
}
</script>


<style lang="stylus" scoped>
$rectangle-size = 0
$border-size = 60px

.triangle-rendering
  width 100%
  height 100%
  display flex
  align-items center
  justify-content center

.triangle
  width $rectangle-size
  height $rectangle-size
  border $border-size solid transparent
</style>
