<template>
  <div>
    <PieChart :options="chartOptions" />
  </div>
</template>

<script>
import PieChart from "jscharting-vue";

export default {
  components: { PieChart },
  data() {
    return {
      chartOptions: {
        legend: {
          position: "inside left bottom",
          template: "%value {%percentOfTotal:n1}% %icon %name"
        },
        title_position: "center",
        defaultSeries_type: "pieDonut",
        defaultPoint_label_text: "<b>%name</b>",
        title_label_text: "Countries GDP",
        yAxis: { label_text: "GDP", formatString: "n" },
        series: [
          {
            name: "Countries",
            points: [
              { name: "United States", y: 5452500 },
              { name: "Canada", y: 786052 },
              { name: "United Kingdom", y: 477338 },
              { name: "Mexico", y: 155313 }
            ]
          }
        ]
      }
    };
  }
};
</script>
