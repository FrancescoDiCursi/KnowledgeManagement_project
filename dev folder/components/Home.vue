<script>
import MapEu from "../components/MapEu.vue"
import MapItaly from "../components/MapItaly.vue"
import TreemapAnimals from "./TreemapAnimals.vue"
import ParallelPlotAnimals from "./ParallelPlotAnimals.vue"
import LineHunters from "./LineHunters.vue"
import BarSports from "./BarSports.vue"
import D3CirclesAssociazioni from "./D3CirclesAssociazioni.vue"
import D3RectVoti from "./D3RectVoti.vue"

export default {
    name:'Home',
    props:{},
    components:{ MapEu, MapItaly, TreemapAnimals, ParallelPlotAnimals, LineHunters, BarSports, D3CirclesAssociazioni, D3RectVoti },
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
       <D3CirclesAssociazioni></D3CirclesAssociazioni>
       <D3RectVoti></D3RectVoti>
       </b-row>
       asdasd
    </b-container>
</template>

<style>
#Home{
    margin-left: auto;
    margin-right: auto;
    text-align: center;
}
</style>