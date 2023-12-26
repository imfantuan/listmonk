<template>
  <section class="line-chart">
    <canvas class="line-chart-canvas" />
  </section>
</template>

<script>
import Chart from 'chart.js/auto';

const DEFAULT = {
  type: 'line',
  data: {},
  options: {
    responsive: true,
    lineTension: 0.5,
    maintainAspectRatio: false,
    interaction: {
      intersect: false,
      axis: 'index',
    },
    plugins: {
      legend: {
        // display: false,
      },
      tooltip: {
        backgroundColor: '#fff',
        borderColor: '#ddd',
        borderWidth: 1,
        bodyColor: '#666',
        displayColors: true,
        bodyFont: {
          size: 15,
        },
        bodySpacing: 10,
        padding: 10,
      },
    },
    scales: {
      x: {
        grid: {
          display: false,
        },
      },
      y: {
        grid: {
          display: false,
        },
      },
    },
  },
};

export default {
  name: 'LineChart',

  props: {
    data: { type: Object, default: () => { } },
  },

  mounted() {
    const ctx = this.$el.querySelector('.line-chart-canvas');
    this.chart = new Chart(ctx, { ...DEFAULT, data: this.$props.data });
  },
};
</script>
