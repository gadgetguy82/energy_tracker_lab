<template lang="html">
  <div class="">
    <p v-for="data in generationMix">{{data}}</p>
    <GChart type="ColumnChart" :data="chartData" :options="chartOptions"/>
  </div>
</template>

<script>
import {GChart} from "vue-google-charts"

export default {
  name: "google-chart",
  props: ["generationMix"],
  data() {
    return {
      chartData: this.generationMix,
      chartOptions: {
        chart: {
          title: "Energy Chart",
          subtitle: "Energy type along with percentage generated"
        }
      }
    }
  },
  components: {
    GChart
  },
}
</script>

<style lang="css" scoped>
</style>
