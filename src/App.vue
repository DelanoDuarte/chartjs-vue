<template>
  <div id="app">
    <img src="./assets/logo.png">
    <ChartComponent :chartData='data' :chartLabels='labels'/>
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
