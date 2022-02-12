<template>
  <h1>OHHH!!</h1>
  <h1>还有 {{ Math.trunc((targetTime - currentTime) / 1000) }} 秒开学</h1>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      targetTime: new Date(2022, 1, 16, 8, 0, 0),
      currentTime: new Date(),
    };
  },
  mounted: function () {
    const self = this;
    this.timer = setInterval(function () {
      self.currentTime = new Date();
    }, 1000);
  },
  unmounted: function () {
    clearInterval(this.timer);
  },
  computed: {
    remainingTime() {
      return Math.trunc((this.targetTime - this.currentTime) / 1000);
    },
  },
};
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
