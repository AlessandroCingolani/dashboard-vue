<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'MainComponent',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: [ 'January', 'February', 'March'],
        datasets: [ { data: [40, 20, 12] } ]
      },
      chartOptions: {
        maintainAspectRatio: false,
        responsive: true
      }
    }
  }
}
</script>

<template>
  <main>
    <div class="main_container">
      <div class="first">
        <Bar
          id="my-chart-id"
          :options="chartOptions"
          :data="chartData"
        />

      </div>
    </div>
  </main>
</template>



<style lang="scss" scoped>
  .main_container {
    display: grid;
    grid-template-columns: repeat(2,1fr);
    grid-template-rows: 350px 350px 400px 350px;
    .first {
        padding: 20px;
        grid-column: 1/ 3;
      }
  }
</style>