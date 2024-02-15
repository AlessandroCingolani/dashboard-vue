<script>
import { Bar, Doughnut, Line } from "vue-chartjs";
import json from "../data/json/data.json";
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
      myData: json,
      loaded: false,
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
    };
  },

  methods: {
    takeSolar() {
      this.dateNow = new Date();
      this.hour = this.dateNow.getHours() + 1;
      console.log(this.hour);
      this.chartData.datasets[0].data = [];
      for (let i = 0; i < this.hour; i++) {
        this.chartData.datasets[0].data.push(store.solarData[i]);
        console.log(store.solarData[i]);
      }
      console.log(this.chartData.datasets[0].data);
    },
  },
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
            data: store.solarData.slice(0, this.hour),
            fill: true,
            borderColor: "rgb(75, 192, 192)",
            tension: 0.5,
          },
        ],
      };
    },
  },

  async mounted() {
    this.loaded = false;
    try {
      this.myData.MonthlyConnections.forEach((connect) => {
        this.dataLine.datasets[0].data.push(connect.connections);
      });
      this.myData.Devices.forEach((connect) => {
        this.dataDonut.datasets[0].data.push(connect.connections);
      });
      this.myData.UsersAgeRange.forEach((connect) => {
        this.dataBar.datasets[0].data.push(connect.connections);
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
