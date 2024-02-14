<script>
import { Bar } from "vue-chartjs";
import { Doughnut } from "vue-chartjs";
import { Line } from "vue-chartjs";
import json from "../data/json/data.json";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  LineElement,
  ArcElement,
  CategoryScale,
  LinearScale,
  PointElement,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  ArcElement,
  BarElement,
  CategoryScale,
  LinearScale,
  LineElement,
  PointElement
);

export default {
  name: "MainComponent",
  components: { Bar, Doughnut, Line },
  data() {
    return {
      myData: json,
      chartData: {
        labels: ["0-16", "17-25", "26-35", "36-45", "46-60"],
        datasets: [{ data: [100, 20, 12] }],
      },
      dataDonut: {
        labels: ["Android", "iOS", "Windows", "Linux", "macOS"],
        datasets: [
          {
            backgroundColor: ["#41B883", "#E46651", "#00D8FF", "#DD1B16"],
            data: [40, 20, 80, 10],
          },
        ],
      },
      optionsLine: {
        responsive: true,
        maintainAspectRatio: false,
      },
      optionsBar: {
        responsive: true,
        maintainAspectRatio: false,
      },
      optionsDonut: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            position: "right",
          },
        },
      },
      data: {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "Data One",
            backgroundColor: "#f87979",
            data: [40, 39, 10, 40, 39, 80, 40],
          },
        ],
      },
    };
  },
  mounted() {
    console.log(this.myData.MonthlyConnections);
  },
};
</script>

<template>
  <main>
    <div class="main_container">
      <div class="row mb-5">
        <div class="line col">
          <div class="card h-100 text-center">
            <div class="card-header">Monthly Connections</div>
            <div class="card-body">
              <Line :data="data" :options="optionsLine" />
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="bar col-lg-6 mb-5">
          <div class="card h-100 text-center">
            <div class="card-header">User Age Range</div>
            <div class="card-body">
              <Bar id="my-chart-id" :options="optionsBar" :data="chartData" />
            </div>
          </div>
        </div>
        <div class="donut col-lg-6 mb-5">
          <div class="card h-100 text-center">
            <div class="card-header">Operating System</div>
            <div class="card-body h-100">
              <Doughnut :data="dataDonut" :options="optionsDonut" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
.main_container {
  padding: 20px;
  gap: 30px;
  .line {
    height: 400px;
  }
}
</style>
