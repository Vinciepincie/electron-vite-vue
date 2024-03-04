<template>
  <!-- 1.3 Meerder grafieken -->
  <p>Grafiek patient 1</p>
  <div style="background-color: whitesmoke; width: 100%;">
    <LineChart />
  </div>

  <p>Grafiek patient 2</p>
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