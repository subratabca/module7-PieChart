<template>
    <div class="pie-chart">
      <canvas ref="chartCanvas"></canvas>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  
  const chartCanvas = ref(null);
  let chartInstance = null;
  
  onMounted(() => {
    // Sample data for the pie chart
    const data = {
      labels: ['Red', 'Blue', 'Yellow','purple'],
      datasets: [
        {
          data: [10, 20, 30, 40],
          backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56'],
          hoverBackgroundColor: ['#FF6384', '#36A2EB', '#FFCE56'],
        },
      ],
    };
  
    const ctx = chartCanvas.value.getContext('2d');
    chartInstance = new Chart(ctx, {
      type: 'pie',
      data: data,
    });
  });
  
  onBeforeUnmount(() => {
    // Clean up the chart instance when the component is unmounted
    if (chartInstance) {
      chartInstance.destroy();
    }
  });
  </script>
  
  <style scoped>
  .pie-chart {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 300px;
  }
  </style>
  