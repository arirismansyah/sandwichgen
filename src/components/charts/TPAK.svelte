
<script>
    export let counter = 0;
    import {Chart} from "svelte-echarts";
    const options = {
    title: {
        text: 'Persentase Angkatan Kerja Terhadap Penduduk Usia Kerja (TPAK)',
        subtext: 'Agustus 2022 (persen)'
    },
    tooltip: {
        trigger: 'axis',
        axisPointer: {
        type: 'shadow'
        },
        valueFormatter: (value) => Math.abs(value)
    },
    xAxis: {
        type: 'category',
        data: ['15-19 \ntahun','20-24 \ntahun','25-29 \ntahun','30-34 \ntahun','35-39 \ntahun','40-44 \ntahun',
        '45-49 \ntahun','50-54 \ntahun','55-59 \ntahun','60+ \ntahun'],
        axisLabel: {
            show: true,
            rotate: 0,
        },
    },
    yAxis: {
        type: 'value'
    },
    series: [
        {
        data: [28.83,68.01,75.32,76.92,79.12,81.39,81.93,81.15,75.41,54.09],
        type: 'bar',
        itemStyle: {color: 'rgba(255, 128, 0)'},
        showBackground: true,
        backgroundStyle: {
            color: 'rgba(180, 180, 180, 0.2)'
        }
        }
    ]
    };
</script>
<div class="tpak">
    {#key counter}
    <Chart {options} key={counter}/>
    <p class="piramid-desc fs-18 text-justify">
        Persentase Angkatan Kerja Terhadap Penduduk Usia Kerja (TPAK), Agustus 2022
        Dari seluruh penduduk usia kerja (15thn +), persentase angkatan kerja pada 
        <span class="highlight">penduduk usia tua </span> cenderung rendah (54% pada uisia 60 tahun keatas).
      </p>
    {/key}
</div>
  
<style>
    .tpak {
        position: fixed;
        top: 5%;
        right: 10%;
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