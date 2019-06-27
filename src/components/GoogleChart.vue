<template lang="html">
  <div class="">
    <p v-for="type in generationMix">{{type}}</p>
  </div>
</template>

<script>
export default {
  name: "google-chart",
  props: ["generationMix"]
}
</script>

<style lang="css" scoped>
</style>
