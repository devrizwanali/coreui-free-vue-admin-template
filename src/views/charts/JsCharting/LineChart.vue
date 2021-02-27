<template>
  <div>
    <LineChart :options="chartOptions" />
  </div>
</template>

<script>
import LineChart from "jscharting-vue";

export default {
  components: { LineChart },
  data() {
    return {
      chartOptions: {
        type: "line",
        title_label_text: "Line Series Types",
        legend_position: "inside bottom right",
        toolbar_items: {
          "Line Type": {
            type: "select",
            label_style_fontSize: 13,
            margin: 5,
            items: "Line"
          }
        },
        xAxis: { scale_type: "time" },
        series: [
          {
            name: "Purchases",
            points: [
              ["1/1/2020", 29.9],
              ["1/2/2020", 71.5],
              ["1/3/2020", 106.4],
              ["1/6/2020", 129.2],
              ["1/7/2020", 144.0],
              ["1/8/2020", 176.0]
            ]
          }
        ]
      }
    };
  }
};
</script>
