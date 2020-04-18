<template>
  <canvas ref="canvas" id="myChart" width="400" height="130"></canvas>
</template>
<script>
/* eslint-disable no-unused-vars */
import Chart from "chart.js";
export default {
  data: () => ({
    series: {
      name: "focus-by-day",
      data: [25, 50, 30, 25, 60, 75, 25],
      index: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
    },
  }),
  mounted() {
    var ctx = this.$refs["canvas"];
    var self = this;
    this.$nextTick(() => {
      new Chart(ctx, {
        type: "line",
        fill: true,
        data: {
          labels: self.series.index,
          datasets: [
            {
              label: "Focus %",
              data: self.series.data,
              backgroundColor: "#F4A478",
            },
          ],
        },
        options: {
          legend: {
            display: false,
          },
          scales: {
            yAxes: [
              {
                ticks: {
                  beginAtZero: true,
                  maxTicksLimit: 5,
                },
              },
            ],
            xAxes: [
              {
                gridLines: {
                  display: false,
                },
              },
            ],
          },
        },
      });
    });
  },
};
</script>
