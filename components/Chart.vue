<template>
  <div>
    <canvas id="myChart"></canvas>
  </div>
</template>

<script setup lang="ts">
import Chart from "chart.js/auto";

const labels = ["Januari", "Februari", "March", "April", "May", "June"];

const data = {
  labels: labels,
  datasets: [
    {
      label: "My First dataset",
      backgroundColor: "rgb(220, 220, 220)",
      borderColor: "rgb(2555,99,132)",
      data: [15, 20, 25, 10, 10, 30, 45],
    },
  ],
};

const config = {
  type: "bar",
  data: data,
  Options: {},
};

onMounted(() => {
  const myChart = new Chart(document.getElementById("myChart"), config);
});
</script>
