<template>
    <div class="char-component"> 
        <div class="canvas">
          <canvas ref="chart" > </canvas>
        </div>
    </div>
</template>

<script>
import Chart from "chart.js";

export default {
  name: "chart-component",
  props: {
    chartTitle: {},
    chartType: {
      required: true
    },
    chartData: {
      type: [Array],
      required: true
    },
    chartLabels: {
      required: true
    }
  },

  data: () => ({
    chart: ""
  }),

  watch: {
    "data.chartData": () => {
      this.chart.update();
    }
  },

  mounted() {
    this.createChart();
  },

  methods: {
    createChart() {
      this.chart = new Chart(this.$refs.chart, {
        type: this.$props.chartType,
        data: {
          labels: this.$props.chartLabels,
          datasets: [
            {
              data: this.$props.chartData,
              backgroundColor: this.generateRandomColors()
            }
          ]
        },
        options: {
          animations: {
            duration: "1500"
          }
        }
      });
    },

    generateRandomColors() {
      let colors = [];
      debugger;

      for (let index = 0; index < this.chartData.length; index++) {
        let randColor1 = Math.floor(Math.random() * 255 + 1);
        let randColor2 = Math.floor(Math.random() * 255 + 1);
        let randColor3 = Math.floor(Math.random() * 255 + 1);
        let randColor4 = Math.random() * (1 - 0.1) + 0.1;
        let color = `rgba(${randColor1.toString()},${randColor2.toString()},${randColor3.toString()},${randColor4.toString()})`;
        colors.push(color);
        color = undefined;
      }
      return colors;
    }
  }
};
</script>

<style scoped>
.canvas {
  width: 50%;
}
</style>
