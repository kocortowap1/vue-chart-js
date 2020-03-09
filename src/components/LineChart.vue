<template>
  <div class="line-chart">
    <canvas id="line" height="400" width="400"></canvas>
  </div>
</template>

<script>
import Chart from 'chart.js'
export default {
  name: "LineChart",
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
  methods: {
    createChart(elID, chartData, chartOption) {
      const ctx = document.getElementById(elID);
      new Chart(ctx, {
        type: "line",
        data: chartData,
        options: chartOption
      });
    }
  },
  mounted() {
    this.createChart("line", this.data, this.option);
  }
};
</script>

<style>
</style>