<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
    name:'LineHunters',
    data(){
        return{
            n_hunters_df:{}
        }
    },
    mounted(){
        Promise.all([d3.csv('./static/n_cacciatori_1980.csv')]).then((csvs)=>{
            console.log(csvs[0])
            this.n_hunters_df=csvs[0]
        })
    },
    methods:{
        linechart(){
            var trace={
                type:'scatter',
                x:this.n_hunters_df.map(d=>d.Year),
                y:this.n_hunters_df.map(d=>d.Value),
                barmode:false

            }

            var layout={

            }

            var config={
                displayModeBar:false
            }

            Plotly.newPlot('line_n_hunters',[trace],layout,config)
        }
    },
    watch:{
    n_hunters_df:function(){
        this.linechart()
    }
    }
}
</script>

<template>
    <div id="line_n_hunters"></div>
</template>

<style>

</style>