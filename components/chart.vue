<template>
  <div>
    <ClientOnly>
      <Line ref="lineChart" :data="chartData" :options="chartOptions" :height="220" :width="400" />
    </ClientOnly>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Line } from 'vue-chartjs';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  PointElement,
  CategoryScale,
  LinearScale,
} from 'chart.js';

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  LineElement,
  PointElement,
  CategoryScale,
  LinearScale
);

const chartData = ref({
  labels: ['Oct, 2023', 'Nov, 2023', 'Dec, 2023', 'Jan, 2024', 'Feb, 2024', 'Mar, 2024'],
  datasets: [
    {
      label: 'Systolic',
      data: [120, 118, 160, 110, 150, 155],
      borderColor: '#C26EB4',
      backgroundColor: '#C26EB4',
      tension: 0.4,
      borderWidth: 2, // Decrease the thickness of the curve
      pointRadius: 3, // Decrease the size of the points
      pointHoverRadius: 5, // Decrease the size of the points on hover
    },
    {
      label: 'Diastolic',
      data: [110, 65, 105, 90, 70, 75],
      borderColor: '#7E6CAB',
      backgroundColor: '#7E6CAB',
      tension: 0.4,
      borderWidth: 2, // Decrease the thickness of the curve
      pointRadius: 3, // Decrease the size of the points
      pointHoverRadius: 5, // Decrease the size of the points on hover
    },
  ],
});

const chartOptions = ref({
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      display: false, // Hide the legend
    },
    title: {
      display: false,
      text: 'Blood Pressure',
    },
  },
  scales: {
    y: {
      min: 60,
      max: 180,
      ticks: {
        stepSize: 20,
        font:{
          size: 10
        }
      }
    },
    x: {
      ticks: {
        font: {
          size: 9, // Set the desired font size for the x-axis labels
        },
        maxRotation: 0, // Prevent labels from rotating
        minRotation: 0, // Prevent labels from rotating
      },
      grid: {
        display: false, // Hide vertical grid lines
      },
    },
  },


})



const lineChart = ref(null);

onMounted(() => {
  if (lineChart.value) {
    lineChart.value.chartInstance.update(); // Force chart update
  }

  console.log('Chart Options:', chartOptions.value);
  console.log('Chart Data:', chartData.value);
});

</script>
