<template lang="html">
  <div id="app">
    <nav>

    </nav>
    <h1>Energy Tracker</h1>
    <google-chart :generationMix="generationMix"></google-chart>
  </div>
</template>

<script>
import GoogleChart from "./components/GoogleChart.vue";

export default {
  name: "app",
  data() {
    return {
      from: "",
      to: "",
      energyMix: [],
      generationMix: [["Fuel", "Percentage"]]
    }
  },
  mounted() {
    fetch("https://api.carbonintensity.org.uk/generation")
    .then(res => res.json()).then(data => {
      this.from = data.data.from;
      this.to = data.data.to;
      this.energyMix = data.data.generationmix;
      this.generationMix = this.generationMix.concat(this.convertObjectArray());
    });
  },
  methods: {
    convertObjectArray() {
      return this.energyMix.map(energyObject => [energyObject.fuel, parseFloat(energyObject.perc)])
    }
  },
  components: {
    "google-chart": GoogleChart
  }
}
</script>

<style lang="css" scoped>
</style>
