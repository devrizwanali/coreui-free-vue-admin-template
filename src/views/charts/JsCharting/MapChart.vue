<template>
  <div>
    <MapChart :options="chartOptions" />
  </div>
</template>

<script>
import MapChart from "jscharting-vue";

export default {
  components: { MapChart },
  data() {
    return {
      chartOptions: {
        type: "map",
        title_label_text: "Americas",
        legend_position: "inside left top",
        mapping_projection: false,
        series: [
          {
            name: "North America",
            map: "americas.continent:North America"
          },
          {
            map: "americas.continent:South America",
            name: "South America"
          }
        ],
        toolbar_items_resetZoom_position: "inside bottom left"
      }
    };
  }
};
</script>
