<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "LinePrezzi",
  data() {
    return {
      price_df: {},
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/prezzi_ISTAT.csv")]).then((csvs) => {
      console.log(csvs[0]);
      this.price_df = csvs[0];
    });
  },
  methods: {
    linechart() {
      var traces = [];
      var animals = this.price_df.columns.slice(1,-2);
      console.log(animals);
      for (var animal of animals) {
        console.log(animal);
        var vals = this.price_df.map((d) =>d[animal]);
        console.log(vals)
        var trace = {
          type: "markers",
          x: this.price_df.map((d) => d.ANNI),
          y: vals.map(Number),
          barmode: false,
          showlegend: true,
          name:animal.split(' ')[0],
          mode: "lines",
        };
        traces.push(trace);
      }
      /*var text= {
        mode:'text',
        x:[1981],
        y:[65],
        text:'Inzio rallentamento demografico',
        showlegend:false,
        textposition:'top'
      }
      

      

      traces.push(text)*/
      var layout = {
        title:'Prezzo carni (euro per quintale)',
        showlegend:true,
        paper_bgcolor:'rgba(196, 164, 132,0)',
        plot_bgcolor:'rgba(196, 164, 132,0)',
        margin: {
          b:0,

        },        xaxis:{
          automargin:true,
          gridcolor:'rgba(196, 164, 132,0.5)'
        },
        yaxis:{
          gridcolor:'rgba(196, 164, 132,0.5)'
        },
        /*shapes:[
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
        ]*/
      };

      var config = {
        displayModeBar: false,
      };

      Plotly.newPlot("line_prices", traces, layout, config);
    },
  },
  watch: {
    price_df: function () {
      this.linechart();
    },
  },
};
</script>

<template>
<b-container>
  <b-row>  <div id="line_prices"></div>
</b-row>
  <b-row><span class='credits_'>Fonte: <a href="https://www.istat.it/it/files//2019/03/cap_21.pdf">ISTAT</a></span></b-row>
</b-container>
</template>

<style>
</style>