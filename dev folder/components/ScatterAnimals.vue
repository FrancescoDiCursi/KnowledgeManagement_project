<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
    name:'ScatterAnimals',
    data(){
        return{
            animals_csv:{}
        }
    },
    mounted(){
        Promise.all([
            d3.csv('./static/fauna_scatter.csv')
        ]).then((data)=>{
            this.animals_csv=data[0]
            console.log(this.animals_csv)
        })
    },
    methods:{
        draw_scatter(){

            var traces=[]
            var symbols_=['circle','square','diamond','cross','x','triangle-up','triangle_down','pentagon']
            var iucn_l= [... new Set(this.animals_csv.map(d=>d.IUCN))].sort()

            

            console.log(iucn_l)
            for(var i=0;i<iucn_l.length;i++){
            var filt_data=this.animals_csv.filter(d=>d.IUCN==iucn_l[i])
            var animals_names=filt_data.map(d=>d.specie_it.length!=0 ?d.specie_it :d.specie_lat)


            var trace_={
                name:iucn_l[i].split(',').join(' & <br>'),
                x:filt_data.map(d=>+d.Valori),
                y:animals_names,
                type:'scatter',
                mode:'markers',
                hovertemplate:'',

                marker:{
                     size:8,
                symbol:symbols_[i]
                }
            }
            console.log(trace_)
            traces.push(trace_)
            }

            var layout_={
                yaxis:{
                    automargin:true,
                    categoryorder:'category descending'
                },
                xaxis:{
                    automargin:true
                },
                height:10000,
            }
                        Plotly.newPlot('animals_scatter',traces,layout_)

        }
    },
    watch:{
        animals_csv:function (){
            this.draw_scatter()
        }
    }
}
</script>

<template>
    <div id="animals_scatter">

    </div>
</template>

<style>

</style>