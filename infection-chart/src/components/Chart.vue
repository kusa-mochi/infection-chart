<script>
import { Line } from "vue-chartjs";

export default {
  extends: Line,
  name: "chart",
  props: {
    days: {
      type: Number,
      required: true
    },
    numPeople: {
      type: Number,
      required: true
    },
    numMeet: {
      type: Number,
      required: true
    },
    pInfec: {
      type: Number,
      required: true
    },
    y0: {
      type: Number,
      required: false,
      default: 1
    },
    options: {
      type: Object,
      required: false,
      default: null
    }
  },
  mounted() {
    this.renderLineChart();
  },
  computed: {
    chartData() {
      let xLabels = [];
      for (let i = 0; i < this.days; i++) {
        xLabels.push(i + 1);
      }
      let xData = [];
      xData.push(this.y0);
      for (let i = 2; i <= this.days; i++) {
        const preValue = xData[i - 2];
        let nextValue =
          (1 + this.numMeet * this.pInfec) * preValue -
          ((this.numMeet * this.pInfec) / this.numPeople) * preValue * preValue;
        if (nextValue > this.numPeople) {
          nextValue = this.numPeople;
        }
        xData.push(nextValue);
      }
      return {
        labels: xLabels,
        datasets: [
          {
            label: "Line Dataset",
            data: xData,
            borderColor: "#CFD8DC",
            fill: false,
            type: "line",
            lineTension: 0.3
          }
        ]
      };
    }
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  },
  methods: {
    renderLineChart() {
      this.renderChart(
        {
          datasets: [
            {
              label: "Data One",
              backgroundColor: "#f87979",
              data: this.chartData
            }
          ]
        },
        { responsive: true, maintainAspectRatio: false }
      );
    }
  },
  watch: {
    chartData() {
      this._chart.destroy();
      //this.renderChart(this.data, this.options);
      this.renderLineChart();
    }
  }
};
</script>

<style lang="scss" scoped>
/* You can write Sass styles here. */
</style>