<template>
  <JSCharting :options="options" style="height: 90px" />
</template>

<script>
import JSCharting from "jscharting-vue";

export default {
  name: 'CChartLineSimple',
  props: {
    color: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: true
    },
    marker: {
      type: Boolean,
      default: true
    },
    boxPadding: {
      type: Number,
      default: 0
    },
    markerColor: {
      type: String,
      default: 'white'
    }
  },
  data() {
    return {
      options: {
        type: this.type,
        defaultPoint: { 
          color: this.markerColor,
          fill: this.markerColor,
          focusGlow: {
            color: 'white',
            width: this.marker ? 2 : 0
          }
        },
        box_padding_left: this.boxPadding,
        box_padding_right: this.boxPadding,
        box_fill: 'none',
        defaultTooltip: {
          combined: true,
          label_text:'<b>%xValue</b><br>%points',
          fill: 'rgba(0, 0, 0, 0.7)',
          radius: 0,
          outline: {
            color: 'rgba(0, 0, 0, 0.7)'
          },
          label: {
            color: 'white'
          }
        },
        xAxis: {
          visible: false,
        },
        yAxis: {
          visible: false,
        },
        legend_visible: false,
        defaultPoint_marker: { fill: 'none', outline_width: 1, type: 'circle', size: 9 },
        series: [
          {
            line: { color: 'white' },
            defaultPoint_marker_visible: this.marker,
            line_width: 1.2,
            points: [
              { x: 'January', y: 40 },
              { x: 'February', y: 30 },
              { x: 'March', y: 35 },
              { x: 'April', y: 30 },
              { x: 'May', y: 45 },
              { x: 'June', y:  28 },
              { x: 'July', y: 32 },
            ]
          }
        ],
      }
    };
  },
  components: {
    JSCharting
  }
};
</script>
