<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "ParallelPlotAnimals",
  props: {


  },
  data() {
    return {

      sel_info:'Categoria',
          Periodo: [],
        Tipo: [],
        Famiglia:[],
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
      this.Famiglia=csvs[0].map(d=>d.Famiglia)
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
        hoveron: this.sel_info=='Categoria' ?"category" :'color',
        hoverinfo: "all",
        dimensions: [
          {
            label: "Periodo",
            values: this.Periodo.map(String),
            categoryorder: "category ascending",
          },
          {
            label: 'Classe',
            values: this.Famiglia.map(String),
            categoryorder:'category ascending'
          }
          ,
          {
            label: "Famiglia",
            values: this.Tipo.map(String),
            categoryorder: "category ascending",
          },
          {
            label: "Specie",
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
      var layout = {
        paper_bgcolor:'rgba(196, 164, 132,0)',
        plot_bgcolor:'rgba(196, 164, 132,0)',
        font:{
          color:'black'
        },
         width: parent.innerWidth/1.3,
         margin:{

          l:400,
          r:200,
          b:0
        }
        }

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
    sel_info:function(){
      this.parallelCoords()
    }
  },
};
</script>

<template>
<b-container>
  <b-row>
    <b-col>
      <b-form-group id="" v-slot="{ariaDescribedby}">
      <b-form-radio-group id="type_filt_parallel" v-model="sel_info" :options="['Categoria','Colore']" :aria-describedby="ariaDescribedby"></b-form-radio-group>
      </b-form-group>
    </b-col>
  </b-row>
  <b-row>
    <b-col>
  <div id="parallel_"></div>
  </b-col>
  </b-row>
  <b-row>
    <span id="credits_">Fonte: <a href="https://www.normattiva.it/uri-res/N2Ls?urn:nir:stato:legge:1992-02-11;157~art18!vig=">Normattiva</a></span>
    <span id="data_path">(legge 11 febbraio 1992, n.157, articolo 18, comma 1)</span>
  </b-row>
</b-container>
</template>

<style>
#parallel_{
  height: 1000px;
  width:90vw;
  margin-left:-10%;
  color:black !important
}
#type_filt_parallel{
  background-color: rgba(196, 164, 132,0.3);
  color:black !important

}
</style>