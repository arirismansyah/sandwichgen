<script>
  import { Chart } from "svelte-echarts";
  export let counter = 1;

  let options = {
    title: [
      {
        text: "Angka Melek Huruf",
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
        min: 95,
      },
    ],
    series: [
      {
        data: [95.5, 95.66, 95.9, 96, 96.04, 96.35],
        type: "line",
        // color: "rgb(51, 124, 207)",
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
    <div class="melek">
      {#key counter}
        <Chart {options} key={counter} />
      {/key}
    </div>
  </div>
</div>

<style>
  .melek {
    width: 400px;
    height: 400px;
  }
</style>
