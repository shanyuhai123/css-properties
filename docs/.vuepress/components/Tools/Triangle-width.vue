<template>
  <div class="triangle-width">
    <div class="width-inputs">
      <input
        v-model="bottom"
        class="width-input"
        type="number"
        min="0"
        max="180"
        placeholder="底"
        :disabled="!isPositive"
        @change="getBorder"
      >
      <input
        v-model="sideOne"
        class="width-input"
        type="number"
        min="0"
        max="180"
        placeholder="边"
        :disabled="type !== 'isosceles' && type !== 'scalene'"
        @change="getBorder"
      >
      <input
        v-model="sideTwo"
        class="width-input"
        type="number"
        min="0"
        max="180"
        placeholder="侧边"
        :disabled="type !== 'scalene'"
        @change="getBorder"
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "triangle-width",
  props: {
    type: {
      type: String,
      validator: function(val) {
        return ["equilateral", "isosceles", "scalene"].includes(val);
      }
    },
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
    }
  },
  data: () => {
    return {
      bottom: 50,
      sideOne: 50,
      sideTwo: 50,
      borderWidth: '',
      isPositive: false
    };
  },
  watch: {
    direction: {
      handler: function(val) {
        this.isPositive = ["top", "right", "left", "bottom"].includes(val)
        this.getBorder();
      },
      immediate: true
    },
    type: {
      handler: function() {
        this.getBorder();
      }
    }
  },
  methods: {
    getBorder() {
      let direction = this.direction;
      let type = this.type;
      switch(type) {
        case 'equilateral':
          this.calcEquBorder(direction);
          break;
        case 'isosceles':
          this.calcIsoBorder(direction);
          break;
        case 'scalene':
          this.calcScaBorder(direction);
          break;
        default:
          break;
      }

      this.$emit('getBorderWidth', this.borderWidth);
    },
    calcEquBorder(direction) {
      let bottom = this.bottom;
      let height = (bottom / Math.sqrt(3)).toFixed(2);

      switch(direction) {
        case 'top':
          this.borderWidth = `0 ${height}px ${bottom}px`;
          break;
        case 'right':
          this.borderWidth = `${height}px 0 ${height}px ${bottom}px`;
          break;
        case 'bottom':
          this.borderWidth = `${bottom}px ${height}px 0`;
          break;
        case 'left':
          this.borderWidth = `${height}px ${bottom}px ${height}px 0`;
          break;
        default:
          break;
      }
    },
    calcIsoBorder(direction) {
      let bottom = this.bottom;
      let sideOne = this.sideOne;
      let height = (sideOne / 2 * Math.sqrt(3)).toFixed(2);

      switch(direction) {
        case 'top':
          this.borderWidth = `0 ${height}px ${bottom}px`;
          break;
        case 'right':
          this.borderWidth = `${height}px 0 ${height}px ${bottom}px`;
          break;
        case 'bottom':
          this.borderWidth = `${bottom}px ${height}px 0`;
          break;
        case 'left':
          this.borderWidth = `${height}px ${bottom}px ${height}px 0`;
          break;
        case 'top-left':
          this.borderWidth = `0 0 ${sideOne}px ${sideOne}px`;
          break;
        case 'top-right':
          this.borderWidth = `0 ${sideOne}px ${sideOne}px 0`;
          break;
        case 'bottom-left':
          this.borderWidth = `${sideOne}px 0 0 ${sideOne}px`;
          break;
        case 'bottom-right':
          this.borderWidth = `0 0 ${sideOne}px ${sideOne}px`;
          break;
        default:
          break;
      }
    },
    calcScaBorder(direction) {
      let bottom = this.bottom;
      let sideOne = this.sideOne;
      let sideTwo = this.sideTwo;

      switch(direction) {
        case 'top':
          this.borderWidth = `0 ${sideOne}px ${bottom}px ${sideTwo}px`;
          break;
        case 'right':
          this.borderWidth = `${sideOne}px 0 ${bottom}px ${sideTwo}px`;
          break;
        case 'bottom':
          this.borderWidth = `${bottom}px ${sideOne}px 0 ${sideTwo}px`;
          break;
        case 'left':
          this.borderWidth = `${sideOne}px ${bottom}px ${sideTwo}px 0`;
          break;
        case 'top-left':
          this.borderWidth = `${sideOne}px ${sideTwo}px 0 0`;
          break;
        case 'top-right':
          this.borderWidth = `0 ${sideOne}px ${sideTwo}px 0`;
          break;
        case 'bottom-left':
          this.borderWidth = `${sideOne}px 0 0 ${sideTwo}px`;
          break;
        case 'bottom-right':
          this.borderWidth = `0 0 ${sideOne}px ${sideTwo}px`;
          break;
        default:
          break;
      }
    }
  }
};
</script>


<style lang="stylus" scoped>
.triangle-width {
  width: 100%;
}

.width-inputs {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-around;

  .width-input {
    width: 22%;
  }
}
</style>

