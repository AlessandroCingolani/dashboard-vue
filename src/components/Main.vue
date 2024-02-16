<script>
import { Bar, Doughnut, Line } from "vue-chartjs";
import json from "../data/json/data.json";
import connections from "../data/json/connections.json";
import { store } from "../data/store";
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
  Filler,
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
  PointElement,
  Filler
);

export default {
  name: "MainComponent",
  components: { Bar, Doughnut, Line },
  data() {
    return {
      store,
      dateNow: "",
      hour: 0,
      updateChartData: [],
      countByAge: {
        "0-16": 0,
        "17-25": 0,
        "26-35": 0,
        "36-45": 0,
        "46-60": 0,
      },
      countByDevice: {
        Android: 0,
        Windows: 0,
        Linux: 0,
        iOs: 0,
      },
      minPercentage: -5,
      maxPercentage: 5,
      myData: json,
      todayConnections: connections,
      loaded: false,
      // Data charts
      dataLine: {
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
            label: "Monthly",
            data: [],
            fill: true,
            borderColor: "rgb(75, 192, 192)",
            tension: 0.5,
          },
        ],
      },
      dataBar: {
        labels: ["0-16", "17-25", "26-35", "36-45", "46-60"],

        datasets: [
          {
            data: [],
            backgroundColor: [
              "rgb(62, 149, 205)",
              "rgb(142, 94, 163)",
              "rgb(90, 187, 159)",
              "rgb(232, 195, 185)",
              "rgb(196, 88, 80)",
            ],
          },
        ],
      },
      dataDonut: {
        labels: ["Android", "iOS", "Windows", "Linux", "macOS"],
        datasets: [
          {
            backgroundColor: [
              "rgb(62, 149, 205)",
              "rgb(142, 94, 163)",
              "rgb(90, 187, 159)",
              "rgb(232, 195, 185)",
              "rgb(196, 88, 80)",
            ],
            data: [],
          },
        ],
      },
      dataGaussian: {
        labels: [
          "0",
          "1",
          "2",
          "3",
          "4",
          "5",
          "6",
          "7",
          "8",
          "9",
          "10",
          "11",
          "12",
          "13",
          "14",
          "15",
          "16",
          "17",
          "18",
          "19",
          "20",
          "21",
          "22",
          "23",
        ],
        datasets: [
          {
            label: "Daily",
            data: [],
            fill: true,
            borderColor: "rgb(75, 192, 192)",
            tension: 0.5,
          },
        ],
      },
      todayAgeBar: {
        labels: ["0-16", "17-25", "26-35", "36-45", "46-60"],

        datasets: [
          {
            data: [],
            backgroundColor: [
              "rgb(62, 149, 205)",
              "rgb(142, 94, 163)",
              "rgb(90, 187, 159)",
              "rgb(232, 195, 185)",
              "rgb(196, 88, 80)",
            ],
          },
        ],
      },
      todayDonut: {
        labels: ["Android", "Windows", "Linux", "iOS"],
        datasets: [
          {
            backgroundColor: [
              "rgb(62, 149, 205)",
              "rgb(142, 94, 163)",
              "rgb(90, 187, 159)",
              "rgb(232, 195, 185)",
            ],
            data: [],
          },
        ],
      },
      // End Data charts

      // Options charts
      optionsLine: {
        responsive: true,
        maintainAspectRatio: false,
      },
      optionsBar: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: false,
          },
        },
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
      optionsGaussian: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          y: {
            type: "linear",
            min: 0,
            max: 100,
          },
        },
      },
      // End options chart
    };
  },

  methods: {
    // Generate random from -5 at 5 to take different solar value
    generateNumber() {
      return Math.floor(
        Math.random() * (this.maxPercentage - this.minPercentage + 1) +
          this.minPercentage
      );
    },
    // At click take hour and generate random solar value display only at hour now
    takeSolar() {
      this.dateNow = new Date();
      this.hour = this.dateNow.getHours() + 1;
      this.updateChartData = [];
      for (let i = 0; i < this.hour; i++) {
        let percentage = this.generateNumber();
        if (percentage <= 0) {
          let result = store.solarData[i] + percentage;
          if (result > 0 && result <= 100) {
            this.updateChartData.push(result);
          } else {
            this.updateChartData.push(store.solarData[i]);
          }
        } else {
          this.updateChartData.push(store.solarData[i]);
        }
      }
    },
  },
  // Computed refresh datas at change
  computed: {
    chartData() {
      return {
        labels: [
          "0",
          "1",
          "2",
          "3",
          "4",
          "5",
          "6",
          "7",
          "8",
          "9",
          "10",
          "11",
          "12",
          "13",
          "14",
          "15",
          "16",
          "17",
          "18",
          "19",
          "20",
          "21",
          "22",
          "23",
        ],
        datasets: [
          {
            label: "Daily",
            data: this.updateChartData.slice(0, this.hour),
            fill: true,
            borderColor: "rgb(75, 192, 192)",
            tension: 0.5,
          },
        ],
      };
    },
  },
  // Async for take data charts
  async mounted() {
    this.loaded = false;
    try {
      // Data
      this.myData.MonthlyConnections.forEach((connect) => {
        this.dataLine.datasets[0].data.push(connect.connections);
      });
      this.myData.Devices.forEach((connect) => {
        this.dataDonut.datasets[0].data.push(connect.connections);
      });
      this.myData.UsersAgeRange.forEach((connect) => {
        this.dataBar.datasets[0].data.push(connect.connections);
      });
      // Connections

      // if element is in object add +1 at counter corrispondent age
      this.todayConnections.forEach((element) => {
        if (element.age in this.countByAge) {
          this.countByAge[element.age]++;
        }
      });
      // take array of numbers from the object
      let numbers = Object.values(this.countByAge);

      numbers.forEach((number) => {
        this.todayAgeBar.datasets[0].data.push(number);
      });

      // device
      this.todayConnections.forEach((element) => {
        if (element.device in this.countByDevice) {
          this.countByDevice[element.device]++;
        }
      });
      // take array of numbers from the object
      let devices = Object.values(this.countByDevice);

      devices.forEach((number) => {
        this.todayDonut.datasets[0].data.push(number);
      });

      this.loaded = true;
    } catch (e) {
      console.error(e);
    }
  },
};
</script>

<template>
  <main>
    <div class="main_container">
      <div class="row mb-5">
        <!-- Line chart -->
        <div class="line col">
          <div class="card h-100 text-center">
            <div class="card-header bg-white">Monthly Connections</div>
            <div class="card-body">
              <Line v-if="loaded" :data="dataLine" :options="optionsLine" />
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <!-- Bar chart -->
        <div class="bar col-lg-6 mb-5">
          <div class="card h-100 text-center">
            <div class="card-header bg-white">User Age Range</div>
            <div class="card-body">
              <Bar
                v-if="loaded"
                id="my-chart-id"
                :options="optionsBar"
                :data="dataBar"
              />
            </div>
          </div>
        </div>
        <!-- Donut chart -->
        <div class="donut col-lg-6 mb-5">
          <div class="card h-100 text-center">
            <div class="card-header bg-white">Operating System</div>
            <div class="card-body h-100">
              <Doughnut
                v-if="loaded"
                :data="dataDonut"
                :options="optionsDonut"
              />
            </div>
          </div>
        </div>
      </div>

      <!-- Gaussian chart -->
      <div class="d-flex justify-content-center mb-4">
        <div
          @click="takeSolar"
          class="play-btn d-flex justify-content-center align-items-center"
        >
          <i class="fa-solid fa-play"></i>
        </div>
      </div>
      <div class="row mb-5">
        <div class="gaussian col">
          <div class="card h-100 text-center">
            <div class="card-header bg-white">Solar Power</div>
            <div class="card-body">
              <Line
                v-if="loaded"
                :data="chartData"
                :options="optionsGaussian"
              />
            </div>
          </div>
        </div>
      </div>
      <!-- Today -->
      <div class="text-center mb-3">
        <h1>Today</h1>
      </div>
      <div class="row">
        <!-- Bar chart -->
        <div class="bar col-lg-6 mb-5">
          <div class="card h-100 text-center">
            <div class="card-header bg-white">User Age Range</div>
            <div class="card-body">
              <Bar v-if="loaded" :options="optionsBar" :data="todayAgeBar" />
            </div>
          </div>
        </div>
        <!-- Donut chart -->
        <div class="donut col-lg-6 mb-5">
          <div class="card h-100 text-center">
            <div class="card-header bg-white">Operating System</div>
            <div class="card-body h-100">
              <Doughnut
                v-if="loaded"
                :data="todayDonut"
                :options="optionsDonut"
              />
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
  .gaussian {
    height: 600px;
  }
  .play-btn {
    width: 40px;
    height: 40px;
    background-color: white;
    &:hover {
      cursor: pointer;
    }
    i {
      font-size: 1.8rem;
    }
  }
}
</style>
