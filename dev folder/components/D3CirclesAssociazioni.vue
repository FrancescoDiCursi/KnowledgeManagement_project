<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "D3CirclesAssociazioni",
  data() {
    return {
      associazioni_csv: {},
      imgs: [
        "logofidc.png",
        "logo-anlc.png",
        "Logo-Enelcaccia.png",
        "Logo-Arci-Caccia-220x150.png",
        "Logo-Anuu.png",
        "italcaccia-logo.png",
        "logo-EPS.png",
      ],
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/associazioni_venatorie.csv")]).then(
      (csvs) => {
        console.log(csvs[0].map((d) => d["Associazioni venatorie"]));
        this.associazioni_csv = csvs[0];
      }
    );
  },
  methods: {
    draw_circles() {
      var svg = d3.select("#circles_associazioni");
      var colors = d3
        .scaleOrdinal()
        .domain(this.associazioni_csv.map((d) => d["Associazioni venatorie"]))
        .range(d3.schemeTableau10);
      var width = screen.width / 4;
      var height = 700;

      var values_circle = this.associazioni_csv.map(
        (d) => Math.sqrt(d.Associati) / 3
      );



        var node_bg = svg
        .selectAll(".circles_bg")
        .data(this.associazioni_csv)
        .enter()
        .append("circle")
        .attr("class", "circles_bg")
        .attr("cx", width / 3)
        .attr("cy", height / 3)
        .attr("r", (d) => Math.sqrt(d.Associati) / 4)
        //.attr("stroke", (d) => colors(d))
        .attr("fill", (d, i) => colors(d));


      var node = svg
        .selectAll(".circles")
        .data(this.associazioni_csv)
        .enter()
        .append("circle")
        .attr("class", "circles")
        .attr("cx", width / 3)
        .attr("cy", height / 3)
        .attr("r", (d) => Math.sqrt(d.Associati) / 4)
        .attr("stroke", (d) => 'colors(d)')
        .attr("fill", (d, i) => `url(#image${i + 1})`);

      //pos imgs
      var imgs_nodes = document.getElementsByTagName("image");
      console.log(imgs_nodes);

      //simulation

      var simulation = d3
        .forceSimulation()
        .force(
          "center",
          d3
            .forceCenter()
            .x(width / 2)
            .y(height / 2)
        ) // Attraction to the center of the svg area
        .force("charge", d3.forceManyBody().strength(0.1)) // Nodes are attracted one each other of value is > 0
        .force(
          "collide",
          d3.forceCollide().strength(0.02).radius(100).iterations(1)
        ); // Force that avoids circle overlapping


         var simulation_bg = d3
        .forceSimulation()
        .force(
          "center",
          d3
            .forceCenter()
            .x(width / 2)
            .y(height / 2)
        ) // Attraction to the center of the svg area
        .force("charge", d3.forceManyBody().strength(0.1)) // Nodes are attracted one each other of value is > 0
        .force(
          "collide",
          d3.forceCollide().strength(0.02).radius(100).iterations(1)
        ); // Force that avoids circle overlapping


      simulation.nodes(this.associazioni_csv).on("tick", function (d) {
        node
          .attr("cx", function (d, i) {
            //console.log(imgs_nodes[0].style.x=d)
            // imgs_nodes[i].style.x=d.x/10

            return d.x;
          })
          .attr("cy", function (d, i) {
            //imgs_nodes[i].style.y=d.y/5000
            return d.y;
          });
          

          
      });

            simulation_bg.nodes(this.associazioni_csv).on("tick", function (d) {
        node_bg
          .attr("cx", function (d, i) {
            //console.log(imgs_nodes[0].style.x=d)
            // imgs_nodes[i].style.x=d.x/10

            return d.x;
          })
          .attr("cy", function (d, i) {
            //imgs_nodes[i].style.y=d.y/5000
            return d.y;
          });
          

          
      });
    },
  },
  watch: {
    associazioni_csv: function () {
      this.draw_circles();
    },
  },
};
</script>

<template>
  <b-container>
    <b-row>
      <b-col>
        <svg
          id="circles_associazioni"
          width="35rem"
          height="500px"
          viewBox="-100 100 700 500"
        >
          <defs>
            <pattern id="image1" x="0" y="0" height="1" width="1">
              <image
                x="100"
                y="100"
                width="100"
                height="100"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/logofidc.png?raw=true"
              ></image>
            </pattern>

            <pattern id="image2" x="0" y="0" height="1" width="1">
              <image
                x="30"
                y="30"
                width="100"
                height="100"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/logo-anlc.png?raw=true"
              ></image>
            </pattern>

            <pattern id="image3" x="0" y="0" height="1" width="1">
              <image
                x="20"
                y="20"
                width="100"
                height="100"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/Logo-Enelcaccia.png?raw=true"
              ></image>
            </pattern>

            <pattern id="image4" x="0" y="0" height="1" width="1">
              <image
                x="6"
                y="10"
                width="100"
                height="100"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/Logo-Arci-Caccia-220x150.png?raw=true"
              ></image>
            </pattern>

            <pattern id="image5" x="0" y="0" height="1" width="1">
              <image
                x="0"
                y="-5"
                width="80"
                height="100"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/Logo-Anuu.png?raw=true"
              ></image>
            </pattern>

            <pattern id="image6" x="0" y="0" height="1" width="1">
              <image
                x="5"
                y="5"
                width="50"
                height="50"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/italcaccia-logo.png?raw=true"
              ></image>
            </pattern>

            <pattern id="image7" x="0" y="0" height="1" width="1">
              <image
                x="1.5"
                y="1.5"
                width="49"
                height="49"
                xlink:href="https://github.com/FrancescoDiCursi/KnowledgeManagement_project/blob/main/static/imgs/logo-EPS.png?raw=true"
              ></image>
            </pattern>
          </defs>
        </svg>
      </b-col>
    </b-row>
  </b-container>
</template>

<style>
#circles_associazioni {
  width: 30rem;
  position: relative;
  float:bottom;
}
</style>