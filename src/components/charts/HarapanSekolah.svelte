<script>
  import { Chart } from "svelte-echarts";
  export let counter = 1;

  let options = {
    title: [
      {
        text: "Harapan Lama Sekolah",
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
        min: 12.8,
      },
    ],

    series: [
      {
        data: [12.85, 12.91, 12.95, 12.98, 13.08, 13.1],
        type: "line",
        color: "rgb(51, 124, 207)",
        label: {
          show: true,
          position: "top",
        },
      },
    ],
  };
</script>

<div class="card">
  <div class="card-body">
    <div class="sekolah">
      {#key counter}
        <Chart {options} key={counter} />
      {/key}
    </div>
  </div>
</div>

<style>
  .sekolah {
    width: 400px;
    height: 400px;
  }
</style>
