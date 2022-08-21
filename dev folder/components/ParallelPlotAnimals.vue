<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "ParallelPlotAnimals",
  props: {


  },
  data() {
    return {
          Periodo: [],
        Tipo: [],

    Istanze: [],
   
    start: true,


      Periodo_val_animals: [],
      data_length: 0,
    };
  },
  
  mounted(){
    Promise.all([d3.csv('./static/cacciabili.csv')]).then((csvs)=>{
      console.log(csvs[0])
      this.Periodo=csvs[0].map(d=>d.Periodo)
      this.Tipo=csvs[0].map(d=>d.Tipo)
      this.Istanze=csvs[0].map(d=>d.Istanze)

    })
  },
  methods: {
        created() {
    window.addEventListener("resize", this.parallelCoords());
  },
  destroyed() {
    window.removeEventListener("resize", this.parallelCoords());
  },
    parallelCoords() {
      console.log(this.Periodo, this.Tipo, this.Istanze)
/*
      this.Periodo_val_animals = this.Periodo.map((d, i) => {
        return "•) " + this.Periodo[i] + ": " + this.val_animals[i];
      });
*/
      var colors = new Int8Array(this.data_length);
      var colorscale = [
        [0, "gray"],
        [1, "firebrick"],
      ];
      var trace1 = {
        type: "parcats",
        hoveron: "color",
        //hoverinfo: "count+probability",
        dimensions: [
          {
            label: "Periodo",
            values: this.Periodo.map(String),
            categoryorder: "category ascending",
          },
          {
            label: "Tipo",
            values: this.Tipo.map(String),
            categoryorder: "category ascending",
          },
          {
            label: "Istanze",
            values: this.Istanze.map(String),
            categoryorder: "category ascending",
          }
        ],
        //counts: this.val_animals.map(Number),
        line: {
          colorscale: colorscale,
          cmin: 0,
          cmax: 1,
          color: colors,
          shape: "hspline",
        },
      };

      var data = [trace1];

      let height_;
      let num_set=[...new Set(this.Periodo)]

/*
      if (num_set.length <= 25) {
        height_ = 800;
      }else if( (num_set.length >25) && (num_set.length<=50)){
        height_=1000
      } else {
        height_ = 1500;
      }
*/
      var layout = { width: window.innerWidth,margin:{l:400,r:500}}

      Plotly.newPlot("parallel_", data, layout, {displayModeBar: false,});

      var new_color = new Int8Array(this.data_length);
      var plot_div = document.getElementById("parallel_");
      plot_div.on("plotly_click", function (event) {

        var selection = [];
        for (var i = 0; i < event.points.length; i++) {
          if (new_color[event.points[i].pointNumber] == 1) {
            new_color[event.points[i].pointNumber] = 0;
          } else {
            new_color[event.points[i].pointNumber] = 1;
          }
          selection.push(event.points[i].pointNumber);
        }

        Plotly.restyle("parallel_", { "line.color": [new_color] });
      });
    },
  },
  watch: {
   Istanze: function (newVal) { 
      this.data_length = this.Periodo.length;
      this.parallelCoords();
    },
  },
};
</script>

<template>
  <div id="parallel_"></div>
</template>

<style>
#parallel_{
  display: block;
  height: 1000px;
  width:100vw;
  margin-left:-13%
}
</style>