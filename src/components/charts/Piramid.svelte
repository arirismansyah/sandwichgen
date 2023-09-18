
<script>
    import {Chart} from "svelte-echarts";
    const options = {
        title: {
            // text: 'Jumlah Penduduk Per Kelompok Umur',
            // subtext: 'Tahun 2022 (juta jiwa)'
        },
        tooltip: {
            trigger: 'axis',
            axisPointer: {
            type: 'shadow'
            },
            valueFormatter: (value) => Math.abs(value)
        },
        legend: {
            data: ['Laki-Laki', 'Perempuan']
        },
        grid: {
            left: '3%',
            right: '4%',
            bottom: '3%',
            containLabel: true
        },
        xAxis: [
            {
            type: 'value',
            display: false,
            axisTick: {
                show: false
            }
            }
        ],
        yAxis: [
            {
            type: 'category',
            axisTick: {
                show: false
            },
            data: [
                '0–4 tahun',
                '5–9 tahun',
                '10–14 tahun',
                '15–19 tahun',
                '20–24 tahun',
                '25–29 tahun',
                '30–34 tahun',
                '35–39 tahun',
                '40–44 tahun',
                '45–49 tahun',
                '50–54 tahun',
                '55–59 tahun',
                '60–64 tahun',
                '65–69 tahun',
                '70–74 tahun',
                '75+ tahun'
            ]
            }
        ],
  series: [
    {
      name: 'Laki-Laki',
      type: 'bar',
      stack: 'Total',
      label: {
        show: true
      },
      // emphasis: {
      //   focus: 'series'
      // },
      data: [
        11.3, 11.24, 11.36, 11.43, 11.55, 11.49, 11.22, 10.74, 10.21, 9.38,
        8.24, 6.95, 5.49, 4.04, 2.53, 2.23
      ],
      itemStyle: {
          color: '#45C3A0'
        },
      markArea: {
        itemStyle: {
          color: '#FFAE52'
        },
        data: [[{ yAxis: '65–69 tahun' }, { yAxis: '75+ tahun' }]]
      }
    },
    {
      name: 'Perempuan',
      type: 'bar',
      stack: 'Total',
      label: {
        show: true,
        formatter: function (params) {
          return Math.abs(params.value);
        }
      },
      // emphasis: {
      //   focus: 'series'
      // },
      data: [
        -10.79, -10.77, -10.73, -10.73, -10.94, -10.98, -10.85, -10.5, -10.09,
        -9.35, -8.26, -7.02, -5.58, -4.16, -2.74, -2.9
      ],
      itemStyle: {
          color: '#73B0D6'
        },
      showBackground: true,
      backgroundStyle: {
        color: 'rgba(180, 180, 180, 0.0)'
      },
      markArea: {
        itemStyle: {
          color: '#FFAE52'
        },
        data: [[{ yAxis: '0–4 tahun' }, { yAxis: '10–14 tahun' }]]
      }
    }
  ]
};
    let count = 0;
</script>
    <div class="piramid">
        {#key count}
        <Chart {options} key={count}/>
        <p class="piramid-desc fs-18 text-justify">
            Proporsi Penduduk Indonesia Tahun 2022
            <span class="highlight">Lebih dari 30% penduduk Indonesia</span> 
            berada pada usia tidak produktif, yaitu dibawah 15 tahun dan diatas 64 tahun.
        </p>
        {/key}
    </div>
  
<style>
    .piramid {
        position: fixed;
        top: 10%;
        left: 10%;
        width: 30vw;
        height: 50vh;
    }
    .piramid-desc {
        text-align: center;
    }
    .highlight {
        padding: 6px;
        border-radius: 10px;
        background: #45C4A0;
        color: whitesmoke;
        padding: 7px;
        white-space: nowrap;
    }
</style>