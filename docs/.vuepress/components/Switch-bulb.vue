<template>
  <Layout-Layout
    justify-center
    :background-color="bgColor"
  >
    <section class="room">
      <input
        type="checkbox"
        id="toggle"
        class="switch__input"
      >
      <label
        for="toggle"
        class="switch__label"
      ></label>
      <span class="bulb"></span>
    </section>
  </Layout-Layout>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#847c74" // 夜灰
    };
  }
};
</script>

<style lang="stylus" scoped>
.room {
  position: relative;
  width: 100%;
  height: 100%;

  .switch__input {
    width: 0;
    height: 0;
    filter: opacity(0);
    opacity: 0;
    visibility: hidden;
  }
}

.bulb {
  position: absolute;
  left: 200px;
  width: 2px;
  height: 200px;
  color: black;
  background-color: currentColor;
  animation: swing 2s linear infinite alternate;
  transform-origin: 50% 0;

  &::before {
    position: absolute;
    z-index: 9;
    bottom: 0;
    left: 50%;
    content: '';
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 4px 8px 4px;
    border-color: transparent transparent currentColor transparent;
    transform: translate(-50%, 50%);
  }

  &::after {
    position: absolute;
    z-index: 9;
    bottom: -14px;
    left: 50%;
    content: '';
    transform: translate(-50%, 50%);
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 1px solid #503e2a; // 橄榄灰
    box-shadow: 2px 1px 4px rgba(0, 0, 0, 0.3), inset -1px -2px 2px 2px rgba(50, 50, 50, 0.4);
    transition: all 0.4s .1s ease-out;
  }
}

.switch__label {
  position: absolute;
  left: 70%;
  top: 200px;
  width: 40px;
  height: 48px;
  text-align: center;
  cursor: pointer;
  color: #ffffff;
  background-color: currentColor;
  border-radius: 4px;
  box-shadow: inset 0 8px rgba(255, 255, 255, 0.7), inset 0 11px 1px rgba(250, 250, 250, 0.4), inset 0 -4px 2px rgba(0, 0, 0, 0.2), 0 0 0 5px rgba(#363433, 0.5);

  &::before {
    content: '';
    display: inline-block;
    width: 25px;
    height: 4px;
    border-radius: 4px;
    background: rgba(0, 0, 0, 0.1);
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.2);
  }
}

.switch__input:checked ~ .bulb::after {
  background-color: #ffffff;
  border: 1px solid #e2e1e4; // 芡石白
  box-shadow: 0px 0px 12px rgba(255, 255, 255, 0.8), 0px 0px 28px rgba(255, 255, 255, 0.8), 0px 0px 50px rgba(255, 255, 255, 0.5), 0px 0px 70px rgba(255, 255, 255, 0.6), -80px -15px 120px 0px rgba(255, 255, 255, 0.4);
}
.switch__input:checked ~ .switch__label {
  box-shadow: inset 0 -8px rgba(255, 255, 255, 0.7), inset 0 -11px 1px rgba(250, 250, 250, 0.4), inset 0 3px 2px rgba(0, 0, 0, 0.3), 0 0 0 5px rgba(#363433, 0.5);


  &::before {
  background: rgba(#57c3c2, 0.8); // 石绿
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.6);
}
}


@keyframes swing {
  from {
    transform: rotate(1deg);
  }

  to {
    transform: rotate(-1deg);
  }
}
</style>
