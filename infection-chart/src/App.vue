<template>
  <div id="app">
    <div class="param-area">
      <div class="param-item">
        <div class="param-item__label">総人口</div>
        <div class="param-item__input">
          <vue-slider v-model="numPeople" :min="1" :max="10000000000"></vue-slider>
        </div>
      </div>
    </div>
    <div class="chart-area">
      <chart
        ref="resultChart"
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
import VueSlider from "vue-slider-component";
import "vue-slider-component/theme/default.css";
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
    Chart,
    VueSlider
  }
};
</script>

<style lang="scss">
#app {
  .param-area {
    .param-item {
      &__label {
      }
      &__input {
      }
    }
  }
  .chart-area {
  }
}
</style>
