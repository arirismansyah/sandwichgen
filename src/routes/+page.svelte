<script>
  import FloatNav from "../components/nav/FloatNav.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";
  import { bounceOut } from "svelte/easing";
  import {ScrollTrigger} from "gsap/dist/ScrollTrigger";
  // import {ScrollSmoother} from "gsap/dist/ScrollSmoother";

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

  onMount(() => {
    loadJS();
    const tl = gsap.timeline();

    tl
    .to(".person", {top: '70%', ease: "power1", duration: 1})
    .from(".person-bubble", {opacity: 0, duration: 1 })
    .fromTo('.starting-point', {opacity: 0, duration:0.5, y:'-20%'}, 
    {ease: bounceOut, duration: 0.5, y:'100%', opacity: 1});
    
    gsap.registerPlugin(ScrollTrigger)
    gsap.set('.sec-1', {scale: 0});

    // const tlScroll = gsap.timeline({
    //   scrollTrigger: {
    //   trigger: ".starting-point",
    //   pin: true,   // pin the trigger element while active
    //   start: "top top", // when the top of the trigger hits the top of the viewport
    //   end: innerHeight * 1.3, // end after scrolling 500px beyond the start
    //   scrub: 1, // smooth scrubbing, takes 1 second to "catch up" to the scrollbar
    // }});

    gsap.to('.starting-point', {scale: 0, 
    scrollTrigger: {
      trigger:'.start-animate',
      start: 'top top',
      pin: true,
      toggleActions: "play none none reverse",
      end: '+=100',
      id: 'starting',
      onRefresh:(self) => 
        self.progress && self.animation.progress(1)
    }})
    
    gsap.to('.sec-1', {scale: 1, 
    scrollTrigger: {
      trigger:'.start-point',
      start: 'top top',
      toggleActions: "play none none reverse",
      end: '+=200',
      pin: true,
      markers: true,
      scrub: true,
      id: 'section'
    }})

    gsap.to('.person', {top: '20%', scale: 1.5, 
    scrollTrigger: {
      trigger:'.start-point',
      start: 'top top',
      toggleActions: "play none none reverse",
      end: '+=200',
      pin: true,
      markers: true,
      id: 'image'
    }})
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
  <figure>
    <img
      id="person"
      class="w-auto mt-0 person"
      src="/images/illustration/people1_1x.png"
      srcset="/images/illustration/people1_1x.png"
      alt=""
    />
    <div class="talk-bubble tri-right round btm-right person-bubble">
      <div class="talktext">
        <p class="text-center">Hai!, Saya Bhaskara</p>
      </div>
    </div>
  </figure>
  <!-- content sebenarnya -->
  <div class="starting-point">
    <h6 class="display-4 mb-6 pe-xxl-6 fs-64 mb-5">Bhaskara</h6>
    <p class="text-justify fs-30 lh-sm">
      Seorang ayah muda, hidup dalam kondisi ekonomi yang tidak
      menguntungkan.
    </p>
  </div>
  <div class="sec-1">
    <p class="description fs-24">
      <span class="highlight fw-bold">Merawat orangtuanya yang menua</span> telah menguras sumber daya
      finansialnya. Biaya medis yang tak kunjung habis membuatnya merasa
      terjebak dalam utang yang bertambah besar.
    </p>  
  </div>

  <div class="container py-md-16 d-flex" style="height: 500vh;" id="container">
    <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-top mx-50 align-items-top">
      <div class="col p-0">
      </div>
      <!--/column -->
      <div class="col-lg-7 align-item-center">
        <div class="start-animate"></div>
        <!-- <ul class="progress-list mt-3">
          <li class="sec">
            <p class="description fs-24">
              <span class="highlight fw-bold">Merawat orangtuanya yang menua</span> telah menguras sumber daya
              finansialnya. Biaya medis yang tak kunjung habis membuatnya merasa
              terjebak dalam utang yang bertambah besar.
            </p>
            <div class="progressbar line blue" data-value="100" />
          </li>
          <li class="sec">
            <p class="description fs-24">
             Selain itu, <span class="highlight fw-bold">biaya
             pendidikan anak-anaknya</span> semakin membuatnya gelisah karena tidak
             tahu bagaimana akan mencukupinya. 
            </p>
            <div class="progressbar line yellow" data-value="80" />
          </li>
          <li>
            <p class="description fs-24">
              Kondisi ini semakin diperburuk
              dengan penyesuaian jam kerja yang harus ia lakukan untuk <span class="highlight fw-bold">merawat
              keluarganya</span>. 
              Penghasilannya semakin mengecil, dan ia merasa
              seperti <span class="highlight fw-bold">terperangkap</span>
              dalam lingkaran yang tak berujung dari
              masalah keuangan.
            </p>
          </li>
          <li>
            <p class="description fs-24">
              Namun, kendati terpuruk, Bhaskara <span class="highlight fw-bold">tetap berusaha</span> dengan segala
              cara untuk menjaga keluarganya tetap berjalan. Ia tahu bahwa cinta
              dan komitmen yang ia miliki terhadap keluarganya adalah kekuatan
              yang bisa membantu mereka melalui masa-masa sulit ini.
            </p>
          </li>
          <li>
            <p class="description fs-24">
              Meskipun
              suasana bisa gelap, ia tetap mencari <span class="highlight fw-bold">jalan untuk keluar</span> dan
              mencari bantuan yang diperlukan untuk mengatasi tantangan
              <span class="highlight fw-bold">ekonominya</span>.
            </p>
          </li>
          <li>
            <p class="text-center">
              <b> Tak asing dengan cerita diatas ? </b><br />
              <b
                >Pernahkan kalian bertemu dengan Mardiansah lain di sekitar
                kalian ?</b
              > <br />
              <b>Atau bahkan, kalian bernasib sama dengan Mardiansah ?. </b>
            </p>
            <div class="progressbar line orange" data-value="85" />
            <p class="text-center">
              Ya. Mardiansah adalah satu dari sekian banyak <span
                class="highlight"
              >
                generasi sandwich</span
              > di Indonesia.
            </p>
            <div class="progressbar line green" data-value="90" />
          </li> 
        </ul> -->
        <!-- /.progress-list -->
      </div>
      <!--/column -->
    </div>
    <!--/.row -->
  </div>
  <!-- /.container -->
</section>

<!-- /section -->
<FloatNav />
<!-- <div class="progress-wrap">
  <svg
    class="progress-circle svg-content"
    width="100%"
    height="100%"
    viewBox="-1 -1 102 102"
  >
    <path d="M50,1 a49,49 0 0,1 0,98 a49,49 0 0,1 0,-98" />
  </svg>
</div> -->

<!-- content -->

<style>
/* CSS */
/* html {
  scroll-behavior: smooth;
} */
.person {
  position: fixed;
  left: 10%;
  top: 200%;
  transform: scale(2);
  -webkit-transform-origin: 50% 50%;
  transform-origin: 50% 50%;
}
.starting-point {
  overflow: hidden;
  position: fixed;
  padding-right: 10%;
  width: 60%;
  top: 20% !important;
  left: 40%!important;
}
div[class*=sec] {
  position: fixed;
  padding-right: 10%;
  width: 60%;
  top: 50% !important;
  left: 40%!important;
}
.container {
  overscroll-behavior: none;
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

  .description {
    text-indent: 50px;
    text-align: justify;
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
  background: #45C4A0;
  color: white;
  padding: 6px;
  border-radius: 10px;
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
