<template>
    <div class="char-component"> 
        <h2> {{chartMessage}}</h2>
        <canvas ref="chart" > </canvas>
    </div>
</template>

<script>
import Chart from "chart.js";

export default {
  name: "chart-component",
  props: {
    chartTitle: {},
    chartData: {
      required: true
    },
    chartLabels: {
      required: true
    }
  },

  data: () => ({
    chartMessage: "Chart JS",
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
        type: "pie",
        data: {
          labels: this.$props.chartLabels,
          datasets: [
            {
              data: this.$props.chartData,
              backgroundColor: [
                "rgba(255, 99, 132, 0.2)",
                "rgba(54, 162, 235, 0.2)",
                "rgba(255, 206, 86, 0.2)",
                "rgba(75, 192, 192, 0.2)",
                "rgba(153, 102, 255, 0.2)",
                "rgba(255, 159, 64, 0.2)"
              ]
            }
          ]
        },
        options: {
          animations: {
            duration: "1500"
          }
        }
      });
    }
  }
};
</script>

<style scoped>

</style>
