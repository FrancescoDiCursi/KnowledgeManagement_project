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
    HexCode(color){
        const rgba = color.replace(/^rgba?\(|\s+|\)$/g, '').split(',');
        const hex = `#${((1 << 24) + (parseInt(rgba[0]) << 16) + (parseInt(rgba[1]) << 8) + parseInt(rgba[2])).toString(16).slice(1)}`;
        
        return hex;
    },
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
        paper_bgcolor:'rgba(196, 164, 132,0)',
        plot_bgcolor:'rgba(196, 164, 132,0)',
        margin:{
          b:0,
        },
        xaxis:{
          automargin:true,
          gridcolor:'rgba(196, 164, 132,0.5)'
        },
        yaxis:{
          gridcolor:'rgba(196, 164, 132,0.5)'
        },
        font:{
          color:'black'
        },
        title:'Licenze cacciatori in Italia',
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
  <b-container>
    <b-row>
  <div id="line_n_hunters"></div>
    </b-row>
    <b-row>
      <span class="credits_">Fonte: <a href='https://www.cacciailcacciatore.org/info/opposizione.html'>cacciailcacciatore (ISTAT) </a></span>
    </b-row>
  </b-container>

</template>

<style>

</style>