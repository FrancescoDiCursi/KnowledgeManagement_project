<script>
import * as d3 from "https://cdn.skypack.dev/d3@7";

export default {
    
    name:'ItalyReserveHeat',
    data(){
        return{
            regioni_vals:{},
            riserve_csv:{}
        }
    },
    mounted(){
        Promise.all([d3.csv('./static/riserve-caccia_Italia(heat_format).csv')]).then((csvs)=>{

            this.riserve_csv=csvs[0]
                        console.log(csvs[0],this.riserve_csv.columns.slice(1,-1), Object.entries(csvs[0]))
                        console.log(this.riserve_csv.map((d,i)=>+d.Campania).reduce((a,b)=>a+b))
            var regioni=this.riserve_csv.columns.slice(1)
            console.log(regioni)
            for(var i=0;i<regioni.length;i++){
                this.regioni_vals[regioni[i]]=this.riserve_csv.map((d,j)=>d[regioni[i]]).reduce((a,b)=>+(a)+(+b))
                console.log(this.riserve_csv.map((d,j)=>d[regioni[i]]).reduce((a,b)=>(+a)+(+b)))
            }
            console.log(Object.values(this.regioni_vals))
        })
    },
    methods:{
        draw_heat(){
            var trace={
                x:this.riserve_csv.columns.slice([1]),
                y:this.riserve_csv.map((d,i)=>Object.values(d)[0]),
                z:this.riserve_csv.map((d,i)=>Object.values(d).slice(1)),
                
                type:'heatmap',
                colorbar:{
                    orientation:'v',
                    x:-0.4,
                    color:'black',
                    ticklabelposition:'inside',
                    tickfont:{
                        color:'black',
                        size:12
                    }
                }
            }



            var layout={
                height:500,
                width:700,
                yaxis:{
                    automargin:true,
                                type:'category',
            categoryorder:'category descending',},
                xaxis:{
                    automargin:true,
                    tickangle:90
                },
                annotations:[],
                margin:{
                t:0,
                r:150
                }
            }

            var config={
                displayModeBar:false
            }

            //add annot
            for (var i=0; i<this.riserve_csv.map((d,i)=>Object.values(d)[0]).length;i++){
                for (var j=0; j<this.riserve_csv.columns.slice([1]).length;j++){

                    var color_='white'
                    if (this.riserve_csv.map((d,i)=>Object.values(d).slice(1))[i][j]==0){
                        color_='black'
                    }
                    var result = {
                        xref:'x1',
                        yref:'y1',
                        x:this.riserve_csv.columns.slice([1])[j],
                        y:this.riserve_csv.map((d,i)=>Object.values(d)[0])[i],
                        text:this.riserve_csv.map((d,i)=>Object.values(d).slice(1))[i][j],
                        showarrow:false,
                        font:{
                            color:color_
                        }                    }
                    layout.annotations.push(result)
                }
            }

            Plotly.newPlot('riserve_it_heat',[trace],layout,config)
        },
        draw_marginalx(){
                var trace_marginalx={
                x:this.riserve_csv.columns.slice([1]),
                y:Object.values(this.regioni_vals),
                type:'bar'
            }
                var layout={
                    width:485,
                    height:200,
                    margin:{
                        r:0,
                        b:0,
                        l:95
                    }
                }
                
            var config={
                displayModeBar:false
            }
            Plotly.newPlot('riserve_it_marginalx',[trace_marginalx],layout,config)
        },
                draw_marginaly(){
                var trace_marginaly={
                y:this.riserve_csv.map((d,i)=>Object.values(d)[0]),
                x:this.riserve_csv.map((d,i)=>Object.values(d).slice(1).reduce((a,b)=>(+a)+(+b))),
                type:'bar',
                orientation:'h'
            }
                var layout={
                    height:475,
                    width:200,
                    yaxis:{
                        visible:false,
                        type:'category',
                        categoryorder:'category descending'
                    },
                    margin:{
                        t:0,
                        l:0,
                    },
                    //plot_bgcolor:'transparent'
                }
                
            var config={
                displayModeBar:false
            }
            Plotly.newPlot('riserve_it_marginaly',[trace_marginaly],layout,config)
        }
        
    },
    watch:{
        riserve_csv:function(){
            this.draw_marginalx()
            this.draw_heat()
            this.draw_marginaly()
        }
    }
}
</script>

<template>
   <b-container id="meta_riserve_it_heat">
        <b-row>
       <div id="riserve_it_marginalx"></div>
       </b-row>
       <b-row>
        <b-col>
      <div id="riserve_it_heat"></div>
      </b-col>
      <b-col>
         <div id="riserve_it_marginaly"></div>
         </b-col>
      </b-row>

   </b-container>
</template>

<style >
#riserve_it_heat{
    position:absolute;
}
#riserve_it_marginalx{
    width: 100%;
    margin-left:4rem;
}
#riserve_it_marginaly{
    position: relative;
    float:right;
    left:13.35rem
}
#meta_riserve_it_heat{
    width:35rem;
    margin-left:auto;
    margin-right:auto
}

</style>