<template>
  <div>
    <h1>万般皆是命，半点不由人</h1>
  </div>
</template>

<script>
export default {
  name: "textGradient",
  setup() {
    return {};
  },
};
</script>

<style lang="less" scoped>
div {
  height: 100vh;

  background: #000;
}
h1 {
  font-size: 48px;
  color: #fff;
  margin: auto;
  font-family: Helvetica;
  background-image: linear-gradient(
    75deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 33.33%,
    rgba(255, 255, 255, 0) 66.67%,
    rgba(255, 255, 255, 0) 100%
  );
  background-size: 300% 100%;
  background-position-x: 100%;
  background-clip: text;
  transition: 2s background-position-x ease-in-out;
  color: transparent;
}

h1:hover {
  background-position-x: 0%;
}
</style>
