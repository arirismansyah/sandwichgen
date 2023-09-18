
<script>
    export let counter = 0;
    import {Chart} from "svelte-echarts";
    let options = {
  title: {
    text: 'Proporsi Pendududuk Menurut Umur',
    subtext: '2015-2045 (persen)',
    textStyle: {fontSize: '20'},
    subtextStyle: {fontSize: '15'}
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'cross',
      label: {
        backgroundColor: '#6a7985'
      }
    }
  },
  // toolbox: {
  //   feature: {
  //     saveAsImage: {}
  //   }
  // },
  grid: {
    left: '5%',
    right: '5%',
    bottom: '5%',
    upper: '5%',
    containLabel: true
  },
  xAxis: [
    {
      type: 'category',
      boundaryGap: false,
      data: ['2015', '2020', '2025', '2030', '2035', '2040', '2045']
    }
  ],
  yAxis: [
    {
      type: 'value',
      showGrid: true,
    }
  ],
  series: [
    {
      name: '0-14 tahun',
      type: 'line',
      step: 'end',
      smooth: true,
      color: '#FF9933',
      width: 5,
      stack: 'Total',
      areaStyle: {color : '#FF9933'},
      emphasis: {
        focus: 'series'
      },
      data: [26.0,24.5,23.3,22.4,21.7,21.1,20.7]
    },
    {
      name: '15-64 tahun',
      type: 'line',
      step: 'end',
      color: '#FFBE73',
      width: 4,
      stack: 'Total',
      areaStyle: {color: '#FFe5CC'},
      emphasis: {
        focus: 'series'
      },
      data: [68.3,68.7,68.6,68.0,67.1,66.1,65.2]
    },
    {
      name: '65+',
      type: 'line',
      step: 'end',
      color: '#FF7700',
      width: 5,
      stack: 'Total',
      areaStyle: {
        color: '#FF7700'},
      emphasis: {
        focus: 'series'
      },
      data: [5.7,6.7,8.1,9.6,11.2,12.8,14.1]
    }
  ],
  scales: {
        yAxes: [{
            ticks: {
                fontSize: 40
            }
        }]
    
  }
};
</script>
    <div class="piramid">
        {#key counter}
        <Chart {options} key={counter}/>
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
        top: 20%;
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