<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
    name:'TreemapAnimals',
    data(){
        return{
            ids:[],
            parents:[],
            labels:[],
            values:[],
            window_height:0,
            window_width:0
        }
    },
    created() {
    window.addEventListener("resize", this.draw_treemap);
  },
  destroyed() {
    window.removeEventListener("resize", this.draw_treemap);
  },
        mounted(){
         Promise.all([d3.csv('./static/fauna_hier.csv')]).then((csvs)=>{
      console.log(csvs[0])
      this.ids=csvs[0].map(d=>d.id)
      this.parents=csvs[0].map(d=>d.parent)
      this.labels=csvs[0].map(d=>d.label)
      this.values=csvs[0].map(d=>d.value)
    })
    },
    methods:{

        draw_treemap(){
            var data = [{
      type: "treemap",
      values:this.values,
      ids: this.ids,
      labels: this.labels,
      parents: this.parents,
            insidetextfont: {"size": 90},


    }];

    var layout={
        width:window.innerWidth/1.5,
        height:window.innerHeight
    }

Plotly.newPlot('tree_animals', data,layout);
        }
    },
    watch:{
        values:function(newVal){
            this.draw_treemap()
        },
        window_width:function(newVal){

            this.draw_treemap()
        }
    }
}
</script>

<template>


          <div id="tree_animals">



</div>

</template>

<style>
#tree_animals{margin-left: 5rem;margin-right:auto;width:30rem}
</style>