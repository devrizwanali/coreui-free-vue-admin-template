<template>
  <div id="chartdiv" ref="chartdiv"></div>
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
          year: "1995",
          cars: 1567,
          motorcycles: 683,
          bicycles: 146
        },
        {
          year: "1996",
          cars: 1617,
          motorcycles: 691,
          bicycles: 138
        },
        {
          year: "1997",
          cars: 1630,
          motorcycles: 642,
          bicycles: 127
        },
        {
          year: "1998",
          cars: 1660,
          motorcycles: 699,
          bicycles: 105
        },
        {
          year: "1999",
          cars: 1683,
          motorcycles: 721,
          bicycles: 109
        },
        {
          year: "2000",
          cars: 1691,
          motorcycles: 737,
          bicycles: 112
        },
        {
          year: "2001",
          cars: 1298,
          motorcycles: 680,
          bicycles: 101
        },
        {
          year: "2002",
          cars: 1275,
          motorcycles: 664,
          bicycles: 97
        },
        {
          year: "2003",
          cars: 1246,
          motorcycles: 648,
          bicycles: 93
        },
        {
          year: "2004",
          cars: 1218,
          motorcycles: 637,
          bicycles: 101
        },
        {
          year: "2005",
          cars: 1213,
          motorcycles: 633,
          bicycles: 87
        },
        {
          year: "2006",
          cars: 1199,
          motorcycles: 621,
          bicycles: 79
        },
        {
          year: "2007",
          cars: 1110,
          motorcycles: 210,
          bicycles: 81
        },
        {
          year: "2008",
          cars: 1165,
          motorcycles: 232,
          bicycles: 75
        },
        {
          year: "2009",
          cars: 1145,
          motorcycles: 219,
          bicycles: 88
        },
        {
          year: "2010",
          cars: 1163,
          motorcycles: 201,
          bicycles: 82
        },
        {
          year: "2011",
          cars: 1180,
          motorcycles: 285,
          bicycles: 87
        },
        {
          year: "2012",
          cars: 1159,
          motorcycles: 277,
          bicycles: 71
        }
      ]
    };
  },
  mounted() {
    let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);
    chart.colors.step = 2;
    // Create axes
    chart.data = this.chartData;

    var categoryAxis = chart.xAxes.push(new am4charts.CategoryAxis());
    categoryAxis.dataFields.category = "year";
    categoryAxis.title.text = "Year";
    categoryAxis.renderer.grid.template.location = 0;
    categoryAxis.renderer.minGridDistance = 20;

    categoryAxis.startLocation = 0.5;
    categoryAxis.endLocation = 0.5;

    var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis.title.text = "Percent";
    valueAxis.calculateTotals = true;
    valueAxis.min = 0;
    valueAxis.max = 100;
    valueAxis.strictMinMax = true;
    valueAxis.renderer.labels.template.adapter.add("text", function(text) {
      return text + "%";
    });

    // Create series
    var series = chart.series.push(new am4charts.LineSeries());
    series.dataFields.valueY = "cars";
    series.dataFields.valueYShow = "totalPercent";
    series.dataFields.categoryX = "year";
    series.name = "Cars";

    series.tooltipHTML =
      "<img src='https://www.amcharts.com/lib/3/images/car.png' style='vertical-align:bottom; margin-right: 10px; width:28px; height:21px;'><span style='font-size:14px; color:#000000;'><b>{valueY.value}</b></span>";

    series.tooltip.getFillFromObject = false;
    series.tooltip.background.fill = am4core.color("#FFF");

    series.tooltip.getStrokeFromObject = true;
    series.tooltip.background.strokeWidth = 3;

    series.fillOpacity = 0.85;
    series.stacked = true;

    // static
    series.legendSettings.labelText = "Cars total:";
    series.legendSettings.valueText = "{valueY.close}";

    // hovering
    series.legendSettings.itemLabelText = "Cars:";
    series.legendSettings.itemValueText = "{valueY}";

    var series2 = chart.series.push(new am4charts.LineSeries());
    series2.dataFields.valueY = "motorcycles";
    series2.dataFields.valueYShow = "totalPercent";
    series2.dataFields.categoryX = "year";
    series2.name = "Motorcycles";

    series2.tooltipHTML =
      "<img src='https://www.amcharts.com/lib/3/images/motorcycle.png' style='vertical-align:bottom; margin-right: 10px; width:28px; height:21px;'><span style='font-size:14px; color:#000000;'><b>{valueY.value}</b></span>";

    series2.tooltip.getFillFromObject = false;
    series2.tooltip.background.fill = am4core.color("#FFF");

    series2.tooltip.getStrokeFromObject = true;
    series2.tooltip.background.strokeWidth = 3;

    series2.fillOpacity = 0.85;
    series2.stacked = true;

    // static
    series2.legendSettings.labelText = "Motorcycles total:";
    series2.legendSettings.valueText = "{valueY.close}";

    // hovering
    series2.legendSettings.itemLabelText = "Motorcycles:";
    series2.legendSettings.itemValueText = "{valueY}";

    var series3 = chart.series.push(new am4charts.LineSeries());
    series3.dataFields.valueY = "bicycles";
    series3.dataFields.valueYShow = "totalPercent";
    series3.dataFields.categoryX = "year";
    series3.name = "Bicycles";
    series3.tooltipText = "{name}: [bold]{valueY}[/]";

    series3.tooltipHTML =
      "<img src='https://www.amcharts.com/lib/3/images/bicycle.png' style='vertical-align:bottom; margin-right: 10px; width:28px; height:21px;'><span style='font-size:14px; color:#000000;'><b>{valueY.value}</b></span>";

    series3.tooltip.getFillFromObject = false;
    series3.tooltip.background.fill = am4core.color("#FFF");

    series3.tooltip.getStrokeFromObject = true;
    series3.tooltip.background.strokeWidth = 3;

    series3.fillOpacity = 0.85;
    series3.stacked = true;

    // static
    series3.legendSettings.labelText = "Bicycles total:";
    series3.legendSettings.valueText = "{valueY.close}";

    // hovering
    series3.legendSettings.itemLabelText = "Bicycles:";
    series3.legendSettings.itemValueText = "{valueY}";

    // Add cursor
    chart.cursor = new am4charts.XYCursor();

    // add legend
    chart.legend = new am4charts.Legend();
  }
};
</script>
<style>
#chartdiv {
  width: 100%;
  height: 500px;
}
</style>
