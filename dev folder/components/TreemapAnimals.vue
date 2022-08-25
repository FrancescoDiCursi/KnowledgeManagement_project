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

            ids_iucn:[],
            parents_iucn:[],
            labels_iucn:[],
            values_iucn:[],
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
         Promise.all([d3.csv('./static/fauna_hier.csv'),
         d3.csv('./static/iucn_hier.csv')],).then((csvs)=>{
      console.log(csvs[0])
      this.ids=csvs[0].map(d=>d.id)
      this.parents=csvs[0].map(d=>d.parent)
      this.labels=csvs[0].map(d=>d.label)
      this.values=csvs[0].map(d=>d.value)

    this.ids_iucn=csvs[1].map(d=>d.id)
      this.parents_iucn=csvs[1].map(d=>d.parent)
      this.labels_iucn=csvs[1].map(d=>d.label)
      this.values_iucn=csvs[1].map(d=>d.value)


    })
    },
    methods:{

        draw_treemap(vals_,ids_,labels_,parents_,html_target,l_,r_){
            var data = [{
      type: "treemap",
      values:vals_,
      ids: ids_,
      labels: labels_,
      parents: parents_,
            insidetextfont: {"size": 90},


    }];

    var layout={
        width:window.innerWidth/3,
        height:window.innerHeight,
        margin:{
            l:l_,
            r:r_
        }
    }

Plotly.newPlot(html_target, data,layout,{displayModeBar:false});
        }
    },
    watch:{
        values:function(newVal){
            this.draw_treemap(this.values, this.ids,this.labels,this.parents,'tree_animals1',0,12)
            this.draw_treemap(this.values_iucn, this.ids_iucn,this.labels_iucn,this.parents_iucn,'tree_animals2',12,0)

        },
        window_width:function(newVal){

            //this.draw_treemap()
        }
    }
}
</script>

<template>

        <b-container>
            <b-row>
                <b-col cols="6">
                              <div id="tree_animals1">
            </div>
                </b-col>
                <b-col cols="6">
                    <div id="tree_animals2"></div>
                </b-col>
            </b-row>
        </b-container>


</template>

<style>
#tree_animals{margin-left: 5rem;margin-right:auto;width:30rem}
</style>