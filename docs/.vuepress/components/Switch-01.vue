<template>
  <Layout-Layout
    align-center
    justify-center
    :background-color="bgColor"
  >
    <section class="switch">
      <input
        type="checkbox"
        id="toggle"
        class="switch__input"
        v-model="toggle"
      >
      <label
        for="toggle"
        class="switch__label"
      ></label>
      <span class="switch__loading"></span>
    </section>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      toggle: "",
      bgColor: "#525288", // 野菊紫
      labelColor: "#22202e" // 暗龙蓝紫
    };
  }
};
</script>


<style lang="stylus" scoped>
$switch-height = 60px;
$switch-width = 200px;
$toggle-size = 50px;
$loading-size = 18px;

.switch {
  position: relative;
  width: $switch-width;
  height: $switch-height;
  display: flex;
  align-items: center;
  justify-content: space-between;

  &__input {
    position: absolute;
    width: 0;
    height: 0;
    filter: opacity(0);
    opacity: 0;
  }

  &__label {
    position: relative;
    display: block;
    box-sizing: border-box;
    height: 100%;
    width: 75%;
    padding: 0 5px;
    display: flex;
    align-items: center;
    background: #22202e; // 暗龙蓝紫
    border-radius: ($switch-height / 2);
    cursor: pointer;
    box-shadow: inset 0 5px 4px 2px rgba(0, 0, 0, 0.8), inset -3px -5px 3px 2px rgba(0, 0, 0, 0.4), 0 1px rgba(255, 255, 255, 0.4);
    transition: all 0.5s ease-in-out;

    &::before {
      content: '';
      display: inline-block;
      position: absolute;
      width: $toggle-size;
      height: $toggle-size;
      border-radius: $toggle-size;
      background-color: #61649f; // 山梗紫
      box-shadow: inset 0 3px rgba(255, 255, 255, 0.2), inset -2px -1px rgba(0, 0, 0, 0.7), 0 0 8px rgba(0, 0, 0, 0.3), 0 12px 12px rgba(0, 0, 0, 0.4);
      left: 4%;
      transition: all 0.5s ease-in-out;
    }
  }

  &__loading {
    width: $loading-size;
    height: $loading-size;
    border-radius: $loading-size;
    border: 5px solid #22202e; // 暗龙蓝紫
  }
}

.switch__input:checked ~ .switch__label::before {
  box-shadow: inset -3px 0 5px rgba(255, 255, 255, 0.7), 0 0 8px rgba(0, 0, 0, 0.3), 0 12px 12px rgba(0, 0, 0, 0.4);
  left: 61%;
}

.switch__input:checked ~ .switch__loading {
  border: 5px solid #ffffff;
  border-top-color: transparent;
  animation: loading 1s infinite cubic-bezier(0.1, 0.7, 1.0, 0.1);
}

@keyframes loading {
  to {
    transform: rotate(1.2turn);
  }
}
</style>
