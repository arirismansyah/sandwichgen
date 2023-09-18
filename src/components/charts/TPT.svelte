<script>
  import { Chart } from "svelte-echarts";
  export let counter = 0;

  let options;

  options = {
    legend: {
      orient: "horizontal",
      // top: 'center',
      right: 10,
      top: 580,
      bottom: 20,
    },
    tooltip: {
      trigger: "axis",
      axisPointer: {
        type: "shadow",
      },
    },
    title: [
      {
        text: "Tingkat Pengangguran Terbuka",
        left: "center",
        top: 0,
      },
      {
        text: "Tingkat Pendidikan Yang Ditamatkan ",
        left: "center",
        bottom: 320,
      },
    ],
    xAxis: [
      {
        type: "category",
        gridIndex: 0,
        axisTick: {
          alignWithLabel: true,
        },
        axisLabel: {
          width: 100, //fixed number of pixels
          overflow: "truncate", // or 'break' to continue in a new line
          interval: 0,
        },
        data: [
          "15-19",
          "20-24",
          "25-29",
          "30-34",
          "35-39",
          "40-44",
          "45-49",
          "50-54",
          "55-59",
          "60 keatas",
        ],
      },
      {
        type: "category",
        gridIndex: 1,
        axisTick: { show: false },
        axisLabel: {
          width: 100, //fixed number of pixels
          overflow: "break", // or 'break' to continue in a new line
          interval: 0,
          fontSize: 11,
        },
        data: [
          "Tidak/Belum\nPernah Sekolah",
          "Tidak\nTamat SD",
          "SD/\nSederajat",
          "SMP/\nSederajat",
          "SMA/\nSederajat",
          "D1/DII/DIII",
          "DIV/S1",
          "Profesi",
          "S2/S3",
        ],
      },
    ],
    yAxis: [{ gridIndex: 0 }, { gridIndex: 1, type: "value" }],
    grid: [
      { bottom: "65%", ContainLabel: true },
      { top: "50%", bottom: 80, ContainLabel: true },
    ],
    series: [
      {
        data: [
          { value: 29.08, itemStyle: { color: "rgba(35,118,188,255)" } },
          { value: 17.02, itemStyle: { color: "rgba(35,118,188,255)" } },
          { value: 7.13, itemStyle: { color: "rgba(35,118,188,255)" } },
          { value: 3.7, itemStyle: { color: "rgba(35,118,188,255)" } },
          { value: 2.65, itemStyle: { color: "rgba(35,118,188,255)" } },
          // Gen X
          { value: 2.43, itemStyle: { color: "rgba(7,174,239,255)" } },
          { value: 2.33, itemStyle: { color: "rgba(7,174,239,255)" } },
          { value: 2.38, itemStyle: { color: "rgba(7,174,239,255)" } },
          // Boomers
          { value: 2.37, itemStyle: { color: "rgba(237,125,49,255)" } },
          { value: 2.85, itemStyle: { color: "rgba(237,125,49,255)" } },
        ],
        type: "bar",
        barWidth: "60%",
        label: {
          show: true,
          position: "top",
          fontSize: 10,
        },
      },
      {
        name: "Generasi Millenial",
        type: "bar",
        barGap: 0,
        emphasis: {
          focus: "series",
        },
        data: [1.4, 3.0, 21.83, 22.62, 37.0, 3.52, 10.04, 0.08, 0.47],
        xAxisIndex: 1,
        yAxisIndex: 1,
        label: {
          show: true,
          position: "top",
          fontSize: 10,
        },
        color: "rgba(35,118,188,255)",
      },
      {
        name: "Generasi X",
        type: "bar",
        emphasis: {
          focus: "series",
        },
        data: [3.05, 6.71, 38.01, 17.22, 25.78, 2.25, 6.32, 0.06, 0.61],
        xAxisIndex: 1,
        yAxisIndex: 1,
        label: {
          show: true,
          position: "top",
          fontSize: 10,
        },
        color: "rgba(7,174,239,255)",
      },
      {
        name: "Baby Boomers",
        type: "bar",
        emphasis: {
          focus: "series",
        },
        data: [9.09, 15.91, 47.23, 9.24, 12.18, 1.68, 4.05, 0.04, 0.57],
        xAxisIndex: 1,
        yAxisIndex: 1,
        label: {
          show: true,
          position: "top",
          fontSize: 10,
        },
        color: "rgba(237,125,49,255)",
      },
    ],
  };

  //   option && myChart.setOption(option);
</script>

<div class="card">
  <div class="card-body">
    <div class="tpt">
      {#key counter}
        <Chart {options} key={counter} />
      {/key}
    </div>
  </div>
</div>

<style>
  .tpt {
    width: 800px;
    height: 600px;
  }
</style>
