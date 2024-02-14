<script>
import { Bar } from 'vue-chartjs'
import { Doughnut } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement,ArcElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, ArcElement, BarElement, CategoryScale, LinearScale)

export default {
  name: 'MainComponent',
  components: { Bar,Doughnut },
  data() {
    return {
      chartData: {
        labels: [ '0-16', '17-25', '26-35','36-45','46-60'],
        datasets: [ { data: [100, 20, 12] } ]
      },
      dataDonut : {
        labels: ['Android', 'iOS', 'Windows', 'Linux','macOS'],
        datasets: [
        {
        backgroundColor: ['#41B883', '#E46651', '#00D8FF', '#DD1B16'],
        data: [40, 20, 80, 10]
        } 
        ]
      },
      options :{
        responsive: true,
        maintainAspectRatio: false
      }
    }
  }
}
</script>

<template>
  <main>
    <div class="main_container">
      <div class="first">
      </div>
        <div class="bar">
          <div class="card h-100 text-center">
            <div class="card-header">
              Operating System
            </div>
            <div class="card-body">
              <Bar
                id="my-chart-id"
                :options="options"
                :data="chartData"
              />
            </div>
          </div>
       
        </div>
        <div class="donut">
          <div class="card h-100 text-center">
            <div class="card-header h-25">
              Operating System
            </div>
            <div class="card-body h-75">
              <Doughnut :data="dataDonut" :options="options" />
            </div>
          </div>
        </div>
    </div>
  </main>
</template>



<style lang="scss" scoped>
  .main_container {
    display: grid;
    padding: 20px;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 350px 350px 400px 350px;
    gap: 20px;
    .first {
      grid-column: 1/ 3;
    }
    .bar {
      grid-column: 1;
      grid-row: 2;
    }
    .donut {
      grid-column: 2;
      grid-row: 2;
    }
  }
</style>