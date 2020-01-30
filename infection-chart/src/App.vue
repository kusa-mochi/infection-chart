<template>
  <div id="app">
    <div class="param-area"></div>
    <div class="chart-area">
      <chart days="250" num-people="8000000000" num-meet="1.5" p-infec="0.1" y0="1"></chart>
    </div>
  </div>
</template>

<script>
import Chart from "./components/Chart.vue";
export default {
  name: "app",
  components: {
    Chart
  }
};
</script>

<style lang="scss">
#app {
  .param-area {
  }
  .chart-area {
  }
}
</style>
