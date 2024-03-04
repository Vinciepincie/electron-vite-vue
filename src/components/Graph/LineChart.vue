<template>
  <Line :data="data" :options="options" />
</template>

<script lang="ts">
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend } from 'chart.js';
import { Line } from 'vue-chartjs';

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend);

export default {
  name: 'HeartRateChart',
  components: { Line },
  data() {
    return {
      data: {
        labels: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'],
        datasets: [
          {
            label: 'Heart Rate',
            borderColor: '#f87979',
            backgroundColor: 'transparent',
            data: [80, 85, 70, 75, 80, 85, 80, 95, 100, 85],
            fill: false
          },
          {
            label: 'Blood Pressure',
            borderColor: 'orange',
            backgroundColor: 'transparent',
            data: [120, 130, 125, 120, 115, 110, 105, 100, 95, 90],
            fill: false
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          y: {
            min: 70,
            max: 130
          },
        }
      }
    };
  },
  methods: {
    increment() {
      // deep clone data object.
      const dataCopy = JSON.parse(JSON.stringify(this.data));

      // add 1 label, remove lowest label
      const labels = dataCopy.labels;
      labels.push((parseInt(labels[labels.length - 1]) + 1).toString());
      labels.shift();

      // Add new hearrate data between 70-100, remove lowest data.
      const datasets = dataCopy.datasets;
      datasets[0].data.push(Math.floor(Math.random() * 30) + 70);
      datasets[0].data.shift();

      // Add new blood pressure data between 90-130, remove lowest data.
      datasets[1].data.push(Math.floor(Math.random() * 40) + 90);
      datasets[1].data.shift();

      // set new data
      this.data = dataCopy;

    },
  },
  mounted() {
    setInterval(this.increment, 250);
  }
};
</script>
