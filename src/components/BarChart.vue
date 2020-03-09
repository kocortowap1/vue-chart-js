<template>
  <div class="bar-chart">
    <canvas id="chart" height="400" width="400"></canvas>
  </div>
</template>

<script>
import Chart from 'chart.js'
export default {
  name: "BarChart",
  props: {
    data: {
      required: true,
      type: Object,
      default: () => {}
    }, 
    option: {
        required: false,
        type: Object,
        default: () => {}
    }
  },
  data() {
    return {};
  },
  methods: {
    createChart(elID, chartData, chartOption) {
      const ctx = document.getElementById(elID);
      new Chart(ctx, {
        type: "bar",
        data: chartData,
        options: chartOption
      });
    }
  },
  mounted(){
      this.createChart('chart', this.data, this.option)
  }
};
</script>

<style>
</style>