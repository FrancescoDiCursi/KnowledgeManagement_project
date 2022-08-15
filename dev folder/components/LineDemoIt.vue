<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "LineDemoIt",
  data() {
    return {
      demo_df: {},
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/demografia_storico.csv")]).then((csvs) => {
      console.log(csvs[0]);
      this.demo_df = csvs[0];
    });
  },
  methods: {
    linechart() {
      var traces = [];
      var trace = {
        type: "markers",
        x: this.demo_df.map((d) => d.Anno),
        y: this.demo_df.map((d) => d.Abitanti),
        barmode: false,
        showlegend: false,
        mode:'lines'
      };
      var text= {
        mode:'text',
        x:[1981],
        y:[65],
        text:'Inzio rallentamento demografico',
        showlegend:false,
        textposition:'top'
      }
      

      

      traces.push(trace);
      traces.push(text)
      var layout = {
        margin:{
            r:200
        },
        shapes:[
            {
                type:'line',
                x0:1981,
                x1:1981,
                y0:0,
                y1:65,
                line:{
                    width:2,
                    dash:'dash'
                }

            }
        ]
       
      };

      var config = {
        displayModeBar: false,
      };

      Plotly.newPlot("line_demoIt", traces, layout, config);
    },
  },
  watch: {
    demo_df: function () {
      this.linechart();
    },
  },
};
</script>

<template>
  <div id="line_demoIt"></div>
</template>

<style>
</style>