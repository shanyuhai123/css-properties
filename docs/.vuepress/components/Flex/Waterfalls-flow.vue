<template>
  <Layout-Layout
    :background-color="bgColor"
    class="flex-flow"
  >
    <div
      class="flow-column"
      v-for="m in 5"
      :key="m"
    >
      <div
        class="flow-item"
        v-for="n in 8"
        :key="n"
      ></div>
    </div>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#c0c4c3" // 月影白
    };
  }
};
</script>

<style lang="stylus" scoped>
$flow-columns = 5; // flow 的列数
$flow-items = 8; // flow 每列的个数

// 函数
randomColor(min, max) {
  return floor(math(0, 'random') * (max - min + 1) + min);
}

randomPx(min, max) {
  return floor(math(0, 'random') * (max - min + 1) + min) px;
}

.flex-flow {
  display: flex;
  justify-content: space-between;
  overflow: hidden;

  .flow-column {
    display: flex;
    flex-direction: column;
    flex: 0 0 18.6%;

    .flow-item {
      width: 100%;
      margin: .1rem 0;
    }
  }
}

for column in (1 .. $flow-columns) {
  .flow-column:nth-child({column}) {

    for item in (1 .. $flow-items) {
      .flow-item:nth-child({item}) {
        flex: 0 0 randomPx(30, 100);
        background-color: rgb(
          randomColor(0, 255),
          randomColor(0, 255),
          randomColor(0, 255)
        );
      }
    }
  }
}
</style>
