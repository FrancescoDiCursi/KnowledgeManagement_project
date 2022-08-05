<script>
import MapEu from "../components/MapEu.vue"
import MapItaly from "../components/MapItaly.vue"
import TreemapAnimals from "./TreemapAnimals.vue"
import ParallelPlotAnimals from "./ParallelPlotAnimals.vue"
import LineHunters from "./LineHunters.vue"
import BarSports from "./BarSports.vue"
export default {
    name:'Home',
    props:{},
    components:{ MapEu, MapItaly, TreemapAnimals, ParallelPlotAnimals, LineHunters, BarSports },
    data(){
        return{
            
        }
    },
    mounted(){

    },
    methods:{
        
    },
    watch:{

    }
}
</script>

<template>
    <b-container id='Home'>
        <b-row>

       <MapEu></MapEu>
       <MapItaly></MapItaly>
       <TreemapAnimals></TreemapAnimals>
       <ParallelPlotAnimals></ParallelPlotAnimals>
       <LineHunters></LineHunters>
       <BarSports></BarSports>

       </b-row>
    </b-container>
</template>

<style>
#Home{
    margin-left: auto;
    margin-right: auto;
    text-align: center;
}
</style>