<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h2>{{chartJs}} </h2>

    <div align='center'>
      <ChartComponent :chartTitle="'Pie Chart'" :chartType="'pie'" :chartData='data' :chartLabels='labels'/>
    </div>
    <hr>

    <div align='center'>
      <ChartComponent :chartTitle="'Horizontal Bar Chart'" :chartType="'horizontalBar'" :chartData='data' :chartLabels='labels'/>
    </div>
    <hr>

  </div>
</template>

<script>
import ChartComponent from "./components/ChartComponent";

export default {
  name: "App",
  components: {
    ChartComponent
  },

  data() {
    return {
      chartJs: "Chart JS",
      labels: ["Column1", "Column2", "Column3"],
      data: [51, 82, 97]
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
