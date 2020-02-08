<template>
  <div id="app">
    <div class="param-area">
      <div class="param-item">
        <div class="param-item__label">総人口</div>
        <div class="param-item__input">
          <vue-slider v-model="numPeople" :min="0" :max="10000000000" :interval="100000000"></vue-slider>
        </div>
        <div class="param-item__label">日数</div>
        <div class="param-item__input">
          <vue-slider v-model="days" :min="5" :max="1000"></vue-slider>
        </div>
        <div class="param-item__label">1日当りの平均接触人数</div>
        <div class="param-item__input">
          <vue-slider v-model="numMeet" :min="0" :max="10" :interval="0.1"></vue-slider>
        </div>
        <div class="param-item__label">感染確率</div>
        <div class="param-item__input">
          <vue-slider
            v-model="probInfection"
            :min="0"
            :max="1"
            :interval="0.01"
            :tooltip-formatter="probInfectionToShow"
          ></vue-slider>
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
  computed: {
    probInfectionToShow() {
      return (this.probInfection * 100) + "%";
    }
  },
  components: {
    Chart,
    VueSlider
  }
};
</script>

<style lang="scss">
#app {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: flex-start;
  align-content: flex-start;

  .param-area {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: stretch;

    width: 200px;
    margin-right: 16px;
  }
  .chart-area {
    width: 500px;
  }
}
</style>
