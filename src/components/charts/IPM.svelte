<script>
  import { Chart } from "svelte-echarts";

  export let counter = 0;

  const options = {
    title: [
      {
        text: "Indeks Pembangunan Manusia (IPM)",
        left: 80,
        top: 0,
      },
    ],
    xAxis: [
      {
        type: "category",
        axisTick: {
          alignWithLabel: true,
        },
        data: [2017, 2018, 2019, 2020, 2021, 2022],
      },
    ],
    yAxis: [
      {
        type: "value",
        min: 70,
      },
    ],

    series: [
      {
        data: [70.81, 71.39, 71.92, 71.94, 72.29, 72.91],
        type: "line",
        label: {
          show: true,
          position: "top",
        },
        color: "green",
      },
    ],
  };
</script>

<div class="card">
  <div class="card-body">
    <div class="ipm">
      {#key counter}
        <Chart {options} key={counter} />
      {/key}
    </div>
  </div>
</div>

<style>
  .ipm {
    width: 400px;
    height: 400px;
  }
</style>
