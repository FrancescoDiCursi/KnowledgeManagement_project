<script>
import * as plotly from "https://cdn.plot.ly/plotly-2.11.1.min.js";
import * as d3 from "https://cdn.skypack.dev/d3@7";
export default {
  name: "D3RectVoti",
  data() {
    return {
      voti_csv: {},

      totali: [],
      si: [],
      no: [],
      nulle: [],
      perc_si: [],
      perc_no: [],
      perc_nulle: [],
      affluenze: [43.36, 42.92, 43.11],
      offsets_no: [239.87, 237.64 + 1, 241.87],
      offsets_nulle: [
        239.87 + 15.09 + 1 + 4,
        237.64 + 11.12 + 10,
        241.87 + 10.24 + 7,
      ],
      rect_labels: ["Si", "No", "Bianche o nulle", "Quorum"],
    };
  },
  mounted() {
    Promise.all([d3.csv("./static/referendum_1990.csv")]).then((csvs) => {
      this.voti_csv = csvs[0];
      console.log(csvs[0]);

      this.totali = csvs[0].map((d) => d["Totale elettori"]);
      this.si = csvs[0].map((d) => +d.Si);
      this.no = csvs[0].map((d) => +d.No);
      this.nulle = csvs[0].map((d) => +d["Schede bianche o nulle"]);

      this.totali_perc = csvs[0].map((d) => d["Totale elettori perc"]);
      this.si_perc = csvs[0].map((d) => +d["Si perc"]);
      this.no = csvs[0].map((d) => +d["No perc"]);
      this.nulle_perc = csvs[0].map((d) => +d["Schede bianche o nulle perc"]);

      console.log(
        this.totali_perc,
        this.si_perc,
        this.no_perc,
        this.nulle_perc
      );
    });
  },
  methods: {
    draw_rects() {
      var svg = d3.select("#rects_votes");
      svg
        .selectAll(".el_population")
        .data(this.voti_csv.map((d) => d["Voti totali"]))
        .enter()
        .append("rect")
        .attr("class", "el_population")
        .attr("width", (d, i) => 100 * 6)
        .attr("height", 100)
        .attr("x", (d, i) => 0)
        .attr("y", (d, i) => i * 140)
        .attr("stroke", "black")
        .attr("fill", "beige");
      //quorum line
      svg
        .append("path")
        .attr("class", "quorum")
        .attr("d", `M ${this.offsets_nulle[0] + 35} -30 V 420 h 35`)
        .attr("stroke", "green")
        .attr("fill", "transparent")
        .attr("stroke-width", 3)
        .attr("stroke-dasharray", "6");
      //si line
      svg
        .append("path")
        .attr("class", "no_line")
        .attr("d", `M ${this.offsets_no[0] - 10} 385 V 530 h 101`)
        .attr("stroke", "green")
        .attr("fill", "transparent")
        .attr("stroke-width", 3)
        .attr("stroke-dasharray", "3");
      //no line
      svg
        .append("path")
        .attr("class", "no_line")
        .attr("d", `M ${this.offsets_no[0] + 10} 385 V 500 h 80`)
        .attr("stroke", "red")
        .attr("fill", "transparent")
        .attr("stroke-width", 3)
        .attr("stroke-dasharray", "3");
      //null line
      svg
        .append("path")
        .attr("class", "null_line")
        .attr("d", `M ${this.offsets_nulle[0] +5} 385 V 460 h 68`)
        .attr("stroke", "grey")
        .attr("fill", "transparent")
        .attr("stroke-width", 3)
        .attr("stroke-dasharray", "3");
        //line textes

            svg
            .append('text')
            .attr('class','legend_labels')
            .attr('x',335)
            .attr('y',530)
            .attr('stroke','green')
            .text(this.rect_labels[0])
            .attr('font-size',20)

            svg
            .append('text')
            .attr('class','legend_labels')
            .attr('x',335)
            .attr('y',500)
            .attr('stroke','red')
            .text(this.rect_labels[1])
            .attr('font-size',20)

            svg
            .append('text')
            .attr('class','legend_labels')
            .attr('x',335)
            .attr('y',460)
            .attr('stroke','grey')
            .text(this.rect_labels[2])
            .attr('font-size',20)

            svg
            .append('text')
            .attr('class','legend_labels')
            .attr('x',335)
            .attr('y',420)
            .attr('stroke','green')
            .text(this.rect_labels[3])
            .attr('font-size',20)
      //
      svg
        .selectAll(".vote_el_yes")
        .data(this.voti_csv.map((d) => d["Si perc"]))
        .enter()
        .append("rect")
        .attr("class", "vote_el_yes")
        .attr("width", (d, i) => ((+d * this.affluenze[i]) / 100) * 6)
        .attr("height", 100)
        .attr("x", (d, i) => 0)
        .attr("y", (d, i) => i * 140)
        .attr("stroke", "black")
        .attr("fill", "green");

      svg
        .selectAll(".vote_el_no")
        .data(this.voti_csv.map((d) => d["No perc"]))
        .enter()
        .append("rect")
        .attr("class", "vote_el_no")
        .attr("width", (d, i) => ((+d * this.affluenze[i]) / 100) * 6)
        .attr("height", 100)
        .attr("x", (d, i) => this.offsets_no[i])
        .attr("y", (d, i) => i * 140)
        .attr("stroke", "black")
        .attr("fill", "red");

      svg
        .selectAll(".vote_el_nulle")
        .data(this.voti_csv.map((d) => d["Schede bianche o nulle perc"]))
        .enter()
        .append("rect")
        .attr("class", "vote_el_nulle")
        .attr("width", (d, i) => ((+d * this.affluenze[i]) / 100) * 6)
        .attr("height", 100)
        .attr("x", (d, i) => this.offsets_nulle[i])
        .attr("y", (d, i) => i * 140)
        .attr("stroke", "black")
        .attr("fill", "grey");

      /*
            var svg=d3.select('#rects_votes')
            svg.selectAll('.vote_el')
            .data(this.voti_csv.map(d=>['Voti totali']))
            .enter()
            .append('rect')
            .attr('class','vote_el')
            .attr('width',100)
            .attr('height',100)
            .attr('x',10)
            .attr('y',5)
            .attr('stroke','black')
*/
    },
  },
  watch: {
    voti_csv: function () {
      this.draw_rects();
    },
  },
};
</script>

<template>
  <svg id="rects_votes" width="1000" height="400" viewBox="200 -50 50 600"></svg>
</template>

<style scoped>
</style>