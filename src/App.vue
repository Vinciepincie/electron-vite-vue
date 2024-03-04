<template>
  <p>Grafiek</p>
  <div style="background-color: whitesmoke; width: 100%;">
    <LineChart />
  </div>
</template>

<script lang="ts">
import LineChart from './components/Graph/LineChart.vue'

export default {
  name: 'App',
  components: { LineChart }
}
</script>