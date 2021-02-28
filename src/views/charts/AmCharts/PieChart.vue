<template>
  <div ref="chartdiv" class="pie"></div>
</template>
<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";
import am4themes_dataviz from "@amcharts/amcharts4/themes/dataviz";

am4core.useTheme(am4themes_dataviz);
am4core.useTheme(am4themes_animated);

export default {
  data() {
    return {
      chartData: [
        {
          country: "Lithuania",
          litres: 501.9
        },
        {
          country: "Czechia",
          litres: 301.9
        },
        {
          country: "Ireland",
          litres: 201.1
        },
        {
          country: "Germany",
          litres: 165.8
        },
        {
          country: "Australia",
          litres: 139.9
        },
        {
          country: "Austria",
          litres: 128.3
        },
        {
          country: "UK",
          litres: 99
        }
      ]
    };
  },
  mounted() {
    let chart = am4core.create(this.$refs.chartdiv, am4charts.PieChart);

    chart.data = this.chartData;

    var pieSeries = chart.series.push(new am4charts.PieSeries());
    pieSeries.dataFields.value = "litres";
    pieSeries.dataFields.category = "country";
    pieSeries.slices.template.stroke = am4core.color("#fff");
    pieSeries.slices.template.strokeOpacity = 1;
    pieSeries.hiddenState.properties.opacity = 1;
    pieSeries.hiddenState.properties.endAngle = -90;
    pieSeries.hiddenState.properties.startAngle = -90;
    chart.hiddenState.properties.radius = am4core.percent(0);
  }
};
</script>
<style>
.pie {
  width: 100%;
  height: 500px;
}
</style>
