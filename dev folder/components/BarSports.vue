<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "BarSports",
  data() {
    return {
      sport_csv: {},
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/sport_istat.csv")]).then((csvs) => {
      console.log(csvs[0]);
      this.sport_csv = csvs[0];
    });
  },
  methods: {
    barchart() {
      var traces = [];
      var df_filt = this.sport_csv.filter((f) => f.Anno == 2015);
      console.log(df_filt);
      var colors = ["black", "blue", "green", "orange", "red",];
      var signs=['/','.','x','-','|']
      var classi_età = [...new Set(this.sport_csv.map((d) => d["Età"]))].slice(
        0,
        -1
      ); //senza Totale
      classi_età.forEach((each, i) => {
        var df_filt_temp = df_filt.filter((f) => f["Età"] == each);
        df_filt_temp = df_filt_temp.filter((f) => f.Sesso == "M");
        var temp_ = {
          type: "bar",
          x: df_filt_temp.map((d) => d.Sport),
          y: df_filt_temp.map((d) => Math.sqrt(+d.Valori)),
          name: each,
          barmode: "group",
          showlegend:true,
          hovertemplate: df_filt_temp.map(d=>'UOMINI' + '<br>'+ d.Sport + ':<br> '+ d.Valori),
          marker: {
            pattern: {
              shape: signs[i],
              bgcolor: 'lightblue',
              fillmode: "replace",
                            fgopacity:0.5,
              

            },
            color: colors[0],
          },
        };
        traces.push(temp_);
      });

      classi_età.forEach((each, i) => {
        var df_filt_temp = df_filt.filter((f) => f["Età"] == each);
        df_filt_temp = df_filt_temp.filter((f) => f.Sesso == "F");
        console.log(df_filt_temp);
        var temp_ = {
          type: "bar",
          x: df_filt_temp.map((d) => d.Sport),
          y: df_filt_temp.map((d) => Math.sqrt(+d.Valori)),
          name: each,
          showlegend: true,
          hovertemplate: df_filt_temp.map(d=>'DONNE'+ '<br>'+ d.Sport + ':<br> '+ d.Valori),
                          
          marker: {
            pattern: {
              shape: signs[i],
              bgcolor: "pink",
              fillmode: "replace",
              fgopacity:0.5,

            },
            color: colors[0],
          },
        };
        traces.push(temp_);
      });

    var text={
      mode:'text',
      x:['Caccia'],
      y:[15,15],
      text:['Caccia'],
      textposition:'top',
      showlegend:false,
      textfont:{size:18,color:'firebrick'}
    }

    traces.push(text)

      console.log(traces);

      var layout = {
        xaxis:{
            type:'category',
            categoryorder:'category ascending',
        },
        height:600,
        margin:{
            b:300,
            t:10
        },
        shapes:[
          {type:'rect',
          x0:3.5,
          y0:0,
          x1:4.5,
          y1:15,
          line:{
            color:'firebrick',
            width:3,
            dash:'dashdot'
          }
          }
        ],

      };

      var config = {
        displayModeBar: true,
      };

      Plotly.newPlot("bar_sport", traces, layout, config);
    },
  },
  watch: {
    sport_csv: function () {
      this.barchart();
    },
  },
};
</script>

<template>
  <div id="bar_sport"></div>
</template>

<style>
#bar_sport{

}
</style>