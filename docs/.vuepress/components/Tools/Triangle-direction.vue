<template>
  <div class="triangle-direction">
    <section
      :class="direction.name === 'oblique' ? 'square-t45' : 'square'"
      v-for="(direction, index) in directions"
      :key="index"
    >
      <div
        class="single"
        v-for="(item, index) in direction.single"
        :key="index"
        :class="{active: direction.name + index === active}"
        @click.stop="changeDirection(item, direction.name + index)"
      >
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "triangle-direction",
  data: () => {
    return {
      active: "oblique0",
      directions: [
        {
          name: "oblique",
          single: ["top", "right", "left", "bottom"]
        },
        {
          name: "positive",
          single: ["top-left", "top-right", "bottom-left", "bottom-right"]
        }
      ]
    };
  },
  mounted() {
    this.changeDirection("top", "oblique0");
  },
  methods: {
    changeDirection(val, index) {
      this.active = index;
      this.$emit("getDirection", val);
    }
  }
};
</script>


<style lang="stylus" scoped>
$square-size = 120px;

.triangle-direction {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.square, .square-t45 {
  position: absolute;
  background-color: #fff;
  display: flex;
  flex-flow: row wrap;

  .single {
    width: 50%;
    height: 50%;
    cursor: pointer;

    &:hover {
      background-color: #1781b5; // 釉蓝
    }
  }

  .active {
    background-color: #f03f24; // 胭脂红
  }
}

.square {
  width: ($square-size * 1.1);
  height: ($square-size * 1.1);

  &::before {
    content: '';
    position: absolute;
    z-index: 9;
    width: ($square-size / 1.45);
    height: ($square-size / 1.45);
    background-color: #c0c4c3;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
}

.square-t45 {
  z-index: 2;
  width: $square-size;
  height: $square-size;
  transform: rotate(45deg);
}
</style>

