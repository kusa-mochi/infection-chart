<template>
  <div id="app">
    <div class="param-area"></div>
    <div class="chart-area">
      <chart
        :days="days"
        :num-people="numPeople"
        :num-meet="numMeet"
        :p-infec="probInfection"
        :y0="y0"
      ></chart>
    </div>
  </div>
</template>

<script>
import Chart from "./components/Chart.vue";
export default {
  name: "app",
  data() {
    return {
      days: 250,
      numPeople: 8000000000,
      numMeet: 1.5,
      probInfection: 0.1,
      y0: 1
    };
  },
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
