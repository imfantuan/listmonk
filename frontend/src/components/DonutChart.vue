<template>
  <section class="donut-chart">
    <canvas class="donut-chart-canvas" />
  </section>
</template>

<script>
import Chart from 'chart.js/auto';

const DEFAULT = {
  type: 'doughnut',
  data: {},
  options: {
    responsive: true,
    cutout: '70%',
    plugins: {
      legend: {
        display: false,
      },
      tooltip: {
        backgroundColor: '#fff',
        borderColor: '#ddd',
        borderWidth: 1,
        titleColor: '#666',
        bodyColor: '#666',
        bodyFont: {
          size: 15,
        },
        bodySpacing: 10,
        padding: 10,
      },
    },
  },
};

export default {
  name: 'DonutChart',

  props: {
    data: { type: Object, default: () => { } },
  },

  mounted() {
    const ctx = this.$el.querySelector('.donut-chart-canvas');
    this.chart = new Chart(ctx, { ...DEFAULT, data: this.$props.data });
  },
};
</script>
