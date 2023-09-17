<script>
  import FloatNav from "../components/nav/FloatNav.svelte";
  import TrendChart from "../components/charts/Trend.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";
  import {ScrollTrigger} from "gsap/dist/ScrollTrigger";
  import SplitType from "split-type";

  const loadJS = () => {
    const pluginsJS = document.createElement("script");
    pluginsJS.setAttribute("src", "/assets_template/js/plugins.js");
    document.head.appendChild(pluginsJS);

    const themeJS = document.createElement("script");
    themeJS.setAttribute("src", "/assets_template/js/theme.js");
    document.head.appendChild(themeJS);

    setTimeout(() => {
      theme.init();
      TyperSetup();
    }, 100);
  };

  let showHighlight=false;

  onMount(() => {
    loadJS();
    const splitType = new SplitType('#funfact-title');
    // const splitType = new SplitType("");
    // gsap animation
    gsap.registerPlugin(ScrollTrigger);
    const factor = 8;

    gsap.set('.person', { top: '160%' });
    gsap.set('.trend-chart', { autoAlpha: 0 });

    var sections = gsap.utils.toArray(".section");
    gsap.set('.section', { autoAlpha: 1 })

    var largeTL = gsap.timeline({
      scrollTrigger: { 
        trigger: '.section',
        pin: true,
        scrub: 0.5,
        start: "top top",
        end: "+=" + (sections.length * 100 * factor) + "%",
        // markers: true
      },
    })

    sections.forEach(function(elem,i) {

      gsap.set(".section", {zIndex: (i, target, targets) => targets.length - i});    
      // select the relevant elements  
      var li = elem.querySelectorAll("li");
      // var second = elem.querySelectorAll(".lines.second");
      const tldelay = i > 0 ? i*factor+2 : i;  
      const tweenduration = 1/20 * factor  // -->  1/cumulated duration of all tweens here * factor
      var bgTimeline = gsap.timeline()

      if (elem.id == "first-section") {
        bgTimeline
        .to(elem, { autoAlpha: 1, duration: tweenduration })
        .to(".person", {top: '70%', ease: "power1", duration: tweenduration/2})
        // .from('.person-bubble', {autoAlpha: 0, duration: tweenduration})
        .from('.starting-point', {yPercent: -110, duration: tweenduration, ease:'power2.inOut'})
        .to({}, {duration: tweenduration/2 }) // a little pause in between
        .to('.starting-point', {yPercent: 120, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        // bubble dan gambar
        .to('.person', {top: '30%', left: '0%', scale: 1.5, duration: tweenduration})
        // .to('.person-bubble', {autoAlpha: 0, duration: tweenduration})
        // .to({}, {duration: tweenduration/2 })
        .from('.description.pt-1', {yPercent: -110, duration: tweenduration, ease:'power2.inOut'})
        .to({}, {duration: tweenduration }) // a little pause in between
        .to('.description.pt-1', {yPercent: 110, duration: tweenduration, ease:'power2.inOut'})
        .to({}, {duration: tweenduration }) // a little pause in between
        .from('.description.pt-2', {yPercent: -110, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 }) // a little pause in between
        .to('.description.pt-2', {yPercent: 110, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 }) // a little pause in between
        .from('.description.pt-3', {yPercent: -120, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        .to('.description.pt-3', {yPercent: 120, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        .from('.description.pt-4', {yPercent: -110, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        .to('.description.pt-4', {yPercent: 110, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        // content-3
        .to('.person', {yPercent:-35, xPercent:-15, scale: 0.8, duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .from('.description.pt-5', {yPercent: -110, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        .to('.description.pt-5', {yPercent: 110, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        .from('.description.pt-6', {yPercent: -120, duration: tweenduration, ease:'power2.inOut'}) 
        .to({}, {duration: tweenduration/2 })
        .to(elem, { autoAlpha: 0, duration: tweenduration })
        .to({}, {duration: tweenduration })
      }
      else if (elem.id == "intro-funfact-section") {
        bgTimeline
        .to(elem, { autoAlpha: 1, duration: tweenduration })
        .from(".funfact-bot", {yPercent: 100, ease: "expo", duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .from('#funfact-title .word', {yPercent: -250, stagger: 0.05, delay: 0.05, duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .to("#funfact-title .word", {autoAlpha:0, duration: tweenduration/2})
        .to(".funfact-bot", {yPercent: -100, xPercent: 70, ease: "power1.inOut", scale: 0.4, rotationY: 360, rotationX: 360, duration: tweenduration*4})
        .to({}, {duration: tweenduration/2 })
        .to('.trend-chart', {autoAlpha: 1, duration: tweenduration})
        .from('#chart-desc p', {xPercent: -110, duration:tweenduration, onComplete: () => {
          showHighlight = true;
        }, onReverseComplete: () => {
          showHighlight= false;
        }})
        .to({}, {duration: tweenduration/2 })
        .to('.trend-chart', {autoAlpha: 0, duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .from('.word-text', {yPercent: -500, duration: tweenduration})
        .from('.wordcloud-desc p', {xPercent: 110, duration: tweenduration})
      }

      largeTL.add(bgTimeline, tldelay);
    })



    var endTL = gsap.timeline({
    scrollTrigger: { 
      trigger: '.section',
      pin: '.container',
      scrub: 0.5,
      start: "top top-=" + (sections.length * 100 * factor) + "%",
      end: "+=" + 10 * factor + "%"
    },
    })

    endTL
  });
</script>

<svelte:head>
  <title>Sandwich Generation</title>
  <link rel="stylesheet" href="/assets_template/css/plugins.css" />
  <link rel="stylesheet" href="/assets_template/css/style.css" />
  <link
    rel="preload"
    href="/assets_template/css/fonts/thicccboi.css"
    as="style"
    onload="this.rel='stylesheet'"
  />
</svelte:head>

<section class="wrapper bg-light">
  <div class="section" id="first-section">
    <figure>
      <img
        id="person"
        class="w-auto mt-0 person"
        src="/images/illustration/people1_1x.png"
        srcset="/images/illustration/people1_1x.png"
        alt=""
      />
      <!-- <div class="talk-bubble tri-right round btm-right person-bubble">
        <div class="talktext">
          <p class="text-center">Hai!, Saya Bhaskara</p>
        </div>
      </div> -->
    </figure>

    <div class="container py-md-16 d-flex" id="container">
      <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-top mx-50 align-items-top">
        <div class="col p-0">
        </div>
        <!--/column -->
        <div class="col-lg-7 align-item-center">
          <ul class="progress-list mt-3 content-1">
            <li>
              <div class="starting-point">
                <h6 class="display-4 mb-6 pe-xxl-6 fs-64 mb-5">Bhaskara</h6>
                <p class="text-justify fs-30 lh-sm">
                  Seorang ayah muda, hidup dalam kondisi ekonomi yang tidak
                  menguntungkan.
                </p>
              </div>
            </li>
          </ul>

          <ul class="progress-list mt-3 content-2">
            <li>
              <p class="description fs-24 pt-1">
                <span class="highlight fw-bold">Merawat orangtuanya yang menua</span> telah menguras sumber daya
                finansialnya. Biaya medis yang tak kunjung habis membuatnya merasa
                terjebak dalam utang yang bertambah besar.
              </p>  
            </li>
             <li>
              <p class="description fs-24 pt-2">
              Selain itu, <span class="highlight fw-bold">biaya
              pendidikan anak-anaknya</span> semakin membuatnya gelisah karena tidak
              tahu bagaimana akan mencukupinya. 
              </p>
            </li>
            <li>
              <p class="description fs-24 pt-3">
                Kondisi ini semakin diperburuk
                dengan penyesuaian jam kerja yang harus ia lakukan untuk <span class="highlight fw-bold">merawat
                keluarganya</span>. 
              </p>
            </li>
            <li>
              <p class="description fs-24 pt-4">
                Penghasilannya semakin mengecil, dan ia merasa
                seperti <span class="highlight fw-bold">terperangkap</span>
                dalam lingkaran yang tak berujung dari
                masalah keuangan.
              </p>
            </li>
          </ul>
          <ul class="progress-list mt-3 content-3">
            <li>
              <p class="description fs-24 pt-5">
                Namun, kendati terpuruk, Bhaskara <span class="highlight fw-bold">tetap berusaha</span> dengan segala
                cara untuk menjaga keluarganya tetap berjalan. Ia tahu bahwa cinta
                dan komitmen yang ia miliki terhadap keluarganya adalah kekuatan
                yang bisa membantu mereka melalui masa-masa sulit ini.
              </p>
            </li>
              
            <li>
              <p class="description fs-24 pt-6">
                Meskipun
                suasana bisa gelap, ia tetap mencari <span class="highlight fw-bold">jalan untuk keluar</span> dan
                mencari bantuan yang diperlukan untuk <span class="highlight fw-bold">mengatasi tantangan</span>ekonominya.
              </p>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <div class="section" id="intro-funfact-section">
    <figure>
      <img
        id="funfact-bot"
        class="w-auto mt-0 funfact-bot"
        src="/images/illustration/funfact_bot.png"
        srcset="/images/illustration/funfact_bot.png"
        alt=""
      />
      <!-- <div class="talk-bubble tri-right round btm-right person-bubble">
        <div class="talktext">
          <p class="text-center">Hai!, Saya Bhaskara</p>
        </div>
      </div> -->
    </figure>
    <div class="container py-md-16 d-flex" id="container">
      <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-top mx-50 align-items-top">
        <div class="col-12 align-item-center">
          <div class="funfact-question text-center">
            <p class="fs-56 pt-5 text-center" id="funfact-title">
              Apakah <b>Sandwich Generation</b> <br> menjadi concern di Indonesia?
            </p>
          </div>
          <div class="trend-chart row justify-content-end">
            <div class="col-6">
              <TrendChart isHighlight={showHighlight}/>
            </div>
            <div class="col-6" id="chart-desc">
              <p class="fs-24 pt-5 text-justify">
                Pencarian keyword <q>generasi sandwich</q> mulai <span class="highlight">meningkat di tahun 2020</span> hingga saat ini, 
                menunjukkan <span class="highlight">peningkatan atensi masyarakat</span> terhadap adanya generasi sandwich di Indonesia.
              </p>
            </div>
          </div>
          <div class="keyword-search fs-50">
            <div class="wordcloud">
              <p class="word-text">KESEHATAN</p>
              <p class="word-text">Beban</p>
              <p class="word-text">Keuangan</p>
              <p class="word-text">Generasi Sandwich</p>
              <p class="word-text">Tips</p>
              <p class="word-text">Stop</p>
              <p class="word-text">Putus</p>
            </div>
            <div class="wordcloud-desc">
              <p class="fs-24 pt-5 text-justify">
                Berdasarkan hasil pada <i><strong>Google Trend</strong></i>, kecenderungan atensi penduduk Indonesia terhadap generasi sandwich, diantaranya: 
                terhadap isu <span class="highlight">keuangan</span>, <span class="highlight">kesehatan 
                mental</span>, dan bagaimana  <span class="highlight">memutus rantai generasi sandwich</span>.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- /section -->
<FloatNav />

<style>
/* CSS */
.content-3 {
  position: absolute;
  top: 20%;
  left: 50%;
  width: 100%;
}
.content-2 {
  position: absolute;
  top: 20%;
  left: 35%;
  width: 100%;
}
.content-1 {
  position: absolute;
  top: 40%;
  left: 45%;
  width: 100%;
}
li {
  overflow: hidden;
  position: absolute;
  padding-right: 10%;
  padding-top: 15px;
  width: 60%;
  height: fit-content;
}
.starting-point {
  position: relative;
  margin: 0;
}

.description {
  position: relative;
  margin: 0;
  text-align: justify;
}
section {
  position: absolute;
  top:0;
  left:0;
  width:100%;
  height:100vh;
}
.section {
  position: absolute;
  top:0;
  left:0;
  width:100%;
  height:100vh;
}
.person {
  position: fixed;
  left: 10%;
  top: 70%;
  /* top: 100%; */
  transform: scale(2);
  -webkit-transform-origin: 50% 50%;
  transform-origin: 50% 50%;
}
div[class*=sec] {
  position: fixed;
  padding-right: 10%;
  /* color: white; */
  padding: 15px;
  border-radius: 10px;
}
.container {
  /* overscroll-behavior: none; */
  min-height: 100vh;
}

/* funfact */
#funfact-bot {
  position: fixed;
  left: 20%;
  top: 42%;
  -webkit-transform-origin: 50% 50%;
  transform-origin: 50% 50%;
}
.funfact-question {
  position: fixed;
  left: 10%;
  top: 15%;
  width: 80%;
  overflow: hidden;
}
#funfact-title .line{
  text-align: center;
}
#chart-desc {
  position: fixed;
  width: fit-content;
  height: fit-content;
  overflow: hidden!important;
  left: 50%!important;
  top: 25%;
}
#chart-desc p {
  position: relative;
  text-align: justify;
  width: 80%;
}

/* Wordcloud */
.wordcloud {
  position: absolute;
  top:15%;
  left:10%;
  height: fit-content;
  width: fit-content;
}
.word-text {
 position: relative;
 padding: 0;
 margin: 0;
 text-transform: uppercase;
 font-weight: 1000;
}
.word-text:nth-of-type(1) {
  top: 10%;
  font-size:90px;
  color: #FF8E0E;
}
.word-text:nth-of-type(2) {
  transform: rotate(90deg) translate(220px, 260px);
  font-size:70px;
  color: #EF5B16;
}
.word-text:nth-of-type(3) {
  transform: translate(80px, -230px);
  font-size:120px;
  color: #45C3A0;
}
.word-text:nth-of-type(4) {
  transform: translate(100px, -300px);
  font-size:50px;
  color: #FAB757
}
.word-text:nth-of-type(5) {
  transform: translate(120px, -450px) rotate(315deg);
  font-size:150px;
  color: #833729;
}
.word-text:nth-of-type(6) {
  transform: translate(100px, -570px);
  font-size:60px;
  color: #079E5F;
}
.word-text:nth-of-type(7) {
  transform: translate(50px, -600px);
  font-size:80px;
  color: #73B0D6;
}

.wordcloud-desc {
  position: absolute;
  width: 40%;
  top: 45%;
  left: 50%;
  overflow: hidden;
}

.talk-bubble {
  margin-left: 0px;
  left: 5%;
  bottom: 70% !important;
  display: inline-block;
  position: fixed;
	width: 250px;
	height: auto;
	background-color: lightcoral;
}
.round{
  border-radius: 15px;
	-webkit-border-radius: 15px;
	-moz-border-radius: 15px;
} 
  .tri-right.btm-right:after {
    content: " ";
    position: absolute;
    width: 0;
    height: 0;
    left: auto;
    right: 0px;
    bottom: -10px;
    border: 12px solid;
    border-color: lightcoral lightcoral transparent transparent;
  }

.highlight {
  padding: 6px;
  border-radius: 10px;
  background: #45C4A0;
  color: whitesmoke;
  padding: 7px;
  white-space: nowrap;
}
/* talk bubble contents */
.talktext{
  padding: 1em;
  color: whitesmoke;
	text-align: left;
  line-height: 1.5em;
  font-size: larger;
}
.talktext p{
  /* remove webkit p margins */
  -webkit-margin-before: 0em;
  -webkit-margin-after: 0em;
}
</style>
