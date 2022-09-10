<script>
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "LineMacellazioni",
  props: {},
  data() {
    return {
              scale_sel:true,
      macellazioni_csv: {},
      tipi:[],
      selected:'Peso (n morto)',
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/ISTAT_serie-macellazioni.csv")]).then((csvs) => {
      this.macellazioni_csv = csvs[0];
            this.yrs=  [... new Set(csvs[0].map(d=>d.Anno))]
      this.tipi=[... new Set(csvs[0].map((d) => d.Tipo))]
      this.tipi=this.tipi.sort()

      console.log(csvs[0],this.tipi)
    });
  },
  methods: {
    macellazioni_linechart() {
      var traces_ = [];
              console.log('FFF', this.tipi)

      for (let i = 0; i < this.tipi.length; i++) {
        var filt_df=this.macellazioni_csv.filter(d=>d.Tipo==this.tipi[i])
        filt_df=filt_df.filter(d=>d['Valori tipo']==this.selected)
        console.log(this.scale_sel)
        var scale_=this.scale_sel
        var y_=function(val){if(scale_==true){return Math.sqrt(val)} else{return val} }
        var temp_trace = {
          x: this.yrs.map(d=>+d),
          y: filt_df.map(d=>y_(+d.Valori)),
          hovertemplate: filt_df.map(d=>d.Valori),
          name: this.tipi[i],
          mode: "lines",
        };
        traces_.push(temp_trace);
      }

      var text = {
        x: [2011],
        y: [70,70],
        text: "Escluse macellazioni domestiche",
        mode: "text",

        textposition: "top left",
        showlegend: false,
        textfont: {
          size: 10,
          color: "darkorange",
        },
        name:'Nota 2010/11',
        hovertemplate:'Solo selvaggina'
      };

        var text2 = {
        x: [2014],
        y: [150],
        text: "Escluso sommerso",
        mode: "text",

        textposition: "top",
        showlegend: false,
        textfont: {
          size: 10,
          color: "black",
        },
        name:'Nota 2013/2014',
        hovertemplate:'Tutti'
      };

              var text3 = {
        x: [1914,1918],
        y: [-5],
        text: "Prima Guerra Mondiale",
        mode: "text",

        textposition: "bottom",
        showlegend: false,
        textfont: {
          size: 10,
          color: "black",
        },
        name:'Nota 1914/1918',
        hovertemplate:'Prima Guerra Mondiale'
      };

                    var text4 = {
        x: [1939,1945],
        y: [-5],
        text: "Seconda Guerra Mondiale",
        mode: "text",

        textposition: "bottom",
        showlegend: false,
        textfont: {
          size: 10,
          color: "black",
        },
        name:'Nota 1938/1945',
        hovertemplate:'Seconda Guerra Mondiale'
      };
                   var text5 = {
        x: [1944],
        y: [125],
        text: "Invasione nazista",
        mode: "text",

        textposition: "top",
        showlegend: false,
        textfont: {
          size: 10,
          color: "black",
        },
        name:'Nota 1944',
        hovertemplate:'Invasione nazista'
      };
     traces_.push(text)
     traces_.push(text2)
     traces_.push(text3)
     traces_.push(text4)
     traces_.push(text5)


      var title_
      if(this.selected=='Numero (n capi)'){
        title_='numero capi in migliaia'
      }else{
        title_='peso morto in migliaia di quintali'
      }

      if(this.scale_sel==false){
        title_+=', valori assoluti'
      }
      else{
        title_+=', asse y scalato per radice quadrata'
      }
      var layout = {
        title:
          `Macellazioni (${title_})`,
        hovermode: "x unified",
        hoverlabel: {
          bgcolor: "rgba(0,0,0,0.8)",
          font: { color: "white" },
        },
        paper_bgcolor:'rgba(196, 164, 132,0)',
        plot_bgcolor:'rgba(196, 164, 132,0)',
        font: {
          //family: 'Courier New, monospace',
          //size: 18,
          color: "black",
        },
        margin:{
          b:0,
        },
        yaxis:{
          gridcolor:'rgba(196, 164, 132,0.5)'
        },
        xaxis: {
          gridcolor:'rgba(196, 164, 132,0.5)',
          autorange: true,
          rangeselector: {
            buttons: [
              {
                count: 1,
                label: "1 mese",
                step: "month",
                stepmode: "backward",
              },
              {
                count: 6,
                label: "6 mesi",
                step: "month",
                stepmode: "backward",
              },
              { label:'Tutto',
                 step: "all" },
            ],
          },
          rangeslider: { },
          type: "year", //not working but date it's not significant (only years avaiable), by putting a wrong value, the button doesn't appear but there's no problem with x axis zoom
        },
        shapes: [
    //line vertical
    {
      type: 'line',
      x0: 2011,
      y0: 0,
      x1: 2011,
      y1: 65,
      line: {
        color: 'rgba(255,140,0,0.9)',
        width: 2,
        dash:'dash',
        
      }
    },
        {
      type: 'line',
      x0: 2014,
      y0: 0,
      x1: 2014,
      y1: 145,
      line: {
        color: 'rgba(0,0,0,0.9)',
        width: 2,
        dash:'dash',
        
      }
    },
    {type:'rect',
          x0:1914,
          y0:0,
          x1:1918,
          y1:100,
          line:{
            color:'rgba(0,0,0,0.5)',
            width:3,
            dash:'dot'
          }
      },
       {type:'rect',
          x0:1939,
          y0:0,
          x1:1945,
          y1:100,
          line:{
            color:'rgba(0,0,0,0.5)',
            width:3,
            dash:'dot'
          }
      }, {
      type: 'line',
      x0: 1944,
      y0: 0,
      x1: 1944,
      y1: 120,
      line: {
        color: 'rgba(0,0,0,0.8)',
        width: 2,
        dash:'dash',
        
      }
    }]
    
      };
      Plotly.newPlot("line_macellazioni", traces_, layout,{displayModeBar:false});
    },
    scale_selection(){
        this.scale_sel=!this.scale_sel
        console.log(this.scale_sel)
    }
  },
  watch: {
    tipi: function (newVal) {
      this.macellazioni_linechart();
    },
    selected:function(){
      this.macellazioni_linechart();
    },
    scale_sel:function(){
        this.macellazioni_linechart()
    }
  },
};

//filtering type and scale 
/* 
  <b-radio-group v-model="selected" :options="['Numero (n capi)', 'Peso (n morto)']">
  <b-button @click="scale_selection">{{this.scale_sel==true ?'Valori scalati per radice quadrata' :'Valori assoluti'}}</b-button>

  </b-radio-group>
*/
</script>

<template>
<b-container>
  <b-row>
  <div id="line_macellazioni"></div>

  </b-row>
  <b-row>
    <span class="credits_">Fonte: <a href="https://seriestoriche.istat.it/index.php?id=1&no_cache=1&tx_usercento_centofe%5Bcategoria%5D=13&tx_usercento_centofe%5Baction%5D=show&tx_usercento_centofe%5Bcontroller%5D=Categoria&cHash=e3503d8195dd4231ff53ba078ad5c124">ISTAT, serie storiche</a></span>
    <span class="data_path"> (Zootecnia e pesca => Bestiame macellato serie )</span>
  </b-row>
</b-container>


</template>

<style>
.selector-text{
    fill: black !important
}

</style>
