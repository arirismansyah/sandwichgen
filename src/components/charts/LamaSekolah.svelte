<script>
  import { Chart } from "svelte-echarts";
  export let counter = 1;

  let options = {
    title: [
      {
        text: "Rata-rata Lama Sekolah",
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
        min: 8,
      },
    ],

    series: [
      {
        data: [8.1, 8.17, 8.34, 8.48, 8.54, 8.69],
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
