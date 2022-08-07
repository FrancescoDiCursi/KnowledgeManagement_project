<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "LineHunters",
  data() {
    return {
      n_hunters_df: {},
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/n_cacciatori_1980.csv")]).then((csvs) => {
      console.log(csvs[0]);
      this.n_hunters_df = csvs[0];
    });
  },
  methods: {
    linechart() {
      var traces = [];
      var trace = {
        type: "scatter",
        x: this.n_hunters_df.map((d) => d.Year),
        y: this.n_hunters_df.map((d) => d.Value),
        barmode: false,
        showlegend: false,
      };

      var text = {
        x: [2007,2007],
        y: [3.5,2.5],
        text: "Picco minimo, apparente inversione di tendenza",
        mode: "text",

        textposition: "bottom",
        showlegend: false,
        textfont: {
          size: 10,
          color: "firebrick",
        },
      };

      traces.push(trace);
      traces.push(text);
      var layout = {
        shapes: [
          {
            type: "line",
            x0: 2007,
            y0: 0,
            x1: 2007,
            y1: 1701000,
            line: {
              color: "firebrick",
              width: 4,
              dash: "dashdot",
            },
          },
        ],
      };

      var config = {
        displayModeBar: false,
      };

      Plotly.newPlot("line_n_hunters", traces, layout, config);
    },
  },
  watch: {
    n_hunters_df: function () {
      this.linechart();
    },
  },
};
</script>

<template>
  <div id="line_n_hunters"></div>
</template>

<style>
</style>