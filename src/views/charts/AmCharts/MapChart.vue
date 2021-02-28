<template>
  <div id="chartdiv" ref="chartdiv"></div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4maps from "@amcharts/amcharts4/maps";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";
import am4geodata_worldLow from "@amcharts/amcharts4-geodata/worldLow";
am4core.useTheme(am4themes_animated);

export default {
  mounted() {
    let chart = am4core.create(this.$refs.chartdiv, am4maps.MapChart);

    // Set map definition
    chart.geodata = am4geodata_worldLow;

    // Set projection
    chart.projection = new am4maps.projections.NaturalEarth1();

    // Create map polygon series
    var polygonSeries = chart.series.push(new am4maps.MapPolygonSeries());
    polygonSeries.mapPolygons.template.strokeWidth = 0.5;

    // Exclude Antartica
    polygonSeries.exclude = ["AQ"];

    // Make map load polygon (like country names) data from GeoJSON
    polygonSeries.useGeodata = true;

    // Configure series
    var polygonTemplate = polygonSeries.mapPolygons.template;
    polygonTemplate.tooltipText = "{name}";
    polygonTemplate.fill = chart.colors.getIndex(0);

    // Create hover state and set alternative fill color
    var hs = polygonTemplate.states.create("hover");
    hs.properties.fill = chart.colors.getIndex(2);

    // Create active state
    var activeState = polygonTemplate.states.create("active");
    activeState.properties.fill = chart.colors.getIndex(4);

    // Create an event to toggle "active" state
    polygonTemplate.events.on("hit", function(ev) {
      ev.target.isActive = !ev.target.isActive;
    });

    var graticuleSeries = chart.series.push(new am4maps.GraticuleSeries());
  }
};
</script>

<style scoped>
#chartdiv {
  width: 100%;
  height: 500px;
}
</style>
