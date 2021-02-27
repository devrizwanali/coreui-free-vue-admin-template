<template>
  <BarChart :options="options" class="BarChart"></BarChart>
</template>

<script>
import BarChart from "jscharting-vue";

export default {
  data() {
    return {
      name: "BarChart",
      options: {
        type: "horizontalColumn",
        title_label_text: "Acme Tool Sales",
        yAxis: { label_text: "Units Sold" },
        xAxis_label_text: "Quarter",
        series: [
          {
            name: "Saw",
            id: "s1",
            points: [
              { x: "Q1", y: 230 },
              { x: "Q2", y: 240 },
              { x: "Q3", y: 267 },
              { x: "Q4", y: 238 }
            ]
          },
          {
            name: "Hammer",
            points: [
              { x: "Q1", y: 325 },
              { x: "Q2", y: 367 },
              { x: "Q3", y: 382 },
              { x: "Q4", y: 371 }
            ]
          },
          {
            name: "Grinder",
            points: [
              { x: "Q1", y: 285 },
              { x: "Q2", y: 292 },
              { x: "Q3", y: 267 },
              { x: "Q4", y: 218 }
            ]
          },
          {
            name: "Drill",
            points: [
              { x: "Q1", y: 185 },
              { x: "Q2", y: 192 },
              { x: "Q3", y: 198 },
              { x: "Q4", y: 248 }
            ]
          }
        ]
      }
    };
  },
  components: {
    BarChart
  }
};
</script>

<style>
.BarChart {
  height: 300px;
}
</style>
