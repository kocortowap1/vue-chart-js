<template>
  <div class="home">
    <BarChart :data="chartData" :option="option" />
    <LineChart :data="chartData" :option="option" />
  </div>
</template>

<script>
// import BarChart from "../components/BarChart";
// import LineChart from "../components/LineChart";
import data from "../sample/bulanan.json";

export default {
  name: "Home",
  components: {
    BarChart: () => import("../components/BarChart"),
    LineChart : () => import("../components/LineChart"),
  },
  data() {
    return {
      data: data,
      option: {
        responsive: false,
        title: {
          display: true,
          text: "Statistik Pendaftar Perbulan"
        }
      }
    };
  },
  computed: {
    chartData() {
      const label = this.data.map(d => {
        const formatBln = new Intl.DateTimeFormat("id-ID", { month: "long" });
        const bln = new Date(Date.UTC(2020, Number(d.id_bulan) - 1, 1, 0, 0));
        return formatBln.format(bln);
      });
      // const total = this.data.map(t => Number(t.total));
      const totalL = this.data.map(j => Number(j.L));
      const totalP = this.data.map(j => Number(j.P));

      return {
        labels: label,
        datasets: [
          {
            label: "Laki-laki",
            borderColor: "blue",
            backgroundColor: "lightblue",
            data: totalL,
            fill: true
          },
          {
            label: "Perempuan",
            borderColor: "red",
            backgroundColor: "pink",
            data: totalP,
            fill: true
          }
        ]
      };
    }
  }
};
</script>
