<script>
import MapEu from "../components/MapEu.vue";
import MapItaly from "../components/MapItaly.vue";
import TreemapAnimals from "./TreemapAnimals.vue";
import ParallelPlotAnimals from "./ParallelPlotAnimals.vue";
import LineHunters from "./LineHunters.vue";
import BarSports from "./BarSports.vue";
import D3CirclesAssociazioni from "./D3CirclesAssociazioni.vue";
import D3RectVoti from "./D3RectVoti.vue";
import LineMacellazioni from "./LineMacellazioni.vue";
import MapItalyRiserve from "./MapItalyRiserve.vue";
import ItalyRiserveHeat from "./ItalyRiserveHeat.vue";

export default {
  name: "Home",
  props: {},
  components: {
    MapEu,
    MapItaly,
    TreemapAnimals,
    ParallelPlotAnimals,
    LineHunters,
    BarSports,
    D3CirclesAssociazioni,
    D3RectVoti,
    LineMacellazioni,
    MapItalyRiserve,
    ItalyRiserveHeat
},
  data() {
    return {};
  },
  mounted() {},
  methods: {},
  watch: {},
};
</script>

<template>
  <b-container id="Home">

      <MapEu></MapEu>
      <LineHunters></LineHunters>
      <LineMacellazioni></LineMacellazioni>
      <D3RectVoti></D3RectVoti>

      <MapItaly></MapItaly>
      <BarSports></BarSports>
      <D3CirclesAssociazioni></D3CirclesAssociazioni>

      <TreemapAnimals></TreemapAnimals>
      <ParallelPlotAnimals></ParallelPlotAnimals>
      
      <MapItalyRiserve></MapItalyRiserve>
      <ItalyRiserveHeat></ItalyRiserveHeat>


  </b-container>
</template>

<style>
#Home {
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}
</style>