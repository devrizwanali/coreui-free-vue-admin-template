<template>
  <div>
    <ActivityGuage :options="chartOptions" ref="activityGuage" />
  </div>
</template>

<script>
import ActivityGuage from "jscharting-vue";

export default {
  components: {
    ActivityGuage
  },
  data() {
    return {
      INTERVAL_ID: null,
      chartOptions: {
        type: "gauge ",
        legend: { position: "bottom" },
        animation_duration: 400,
        //Spacing between circular bars
        xAxis_spacingPercentage: 0.1,
        yAxis: {
          line_width: 0,
          scale_range: [0, 100]
        },

        defaultSeries: {
          type: "column roundCaps",
          angle: { sweep: 360, start: -90 },
          shape_innerSize: "30%"
        },
        defaultTooltip_visible: false,
        series: [
          {
            palette: ["#E10715", "#3FDC00", "#3EBAE1"],
            name: "Activities",
            defaultPoint: {
              marker: {
                fill: "white",
                //Outline makes the markers thicker without making them larger
                outline: { width: 0, color: "white" },
                visible: true,
                size: 17
              }
            },
            points: [
              {
                x: "Running",
                id: "r",
                y: 30,
                marker_type: "material/maps/directions-run"
              },
              {
                x: "Walking",
                id: "w",
                y: 25,
                marker_type: "material/maps/directions-walk"
              },
              {
                x: "Biking",
                id: "s",
                y: 20,
                marker_type: "material/maps/directions-bike"
              } //material/maps/hotel
            ]
          }
        ]
      }
    };
  },
};
</script>
