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
    gsap.registerPlugin(ScrollTrigger);
    const factor = 4;

    gsap.set('.description', { autoAlpha: 0 });
    gsap.set('.starting-point', { autoAlpha: 0 });
    gsap.set('.person', { top: '160%' });

    var sections = gsap.utils.toArray("section:not(.end)");

    var largeTL = gsap.timeline({
      scrollTrigger: { 
        trigger: '.container',
        pin: true,
        scrub: 0.5,
        start: "top top",
        end: "+=" + (sections.length * 100 * factor) + "%",
        markers: true
      },
    })

    sections.forEach(function(elem,i) {

      gsap.set(".section", {zIndex: (i, target, targets) => targets.length - i});    

      // select the relevant elements  
      var lines = elem.querySelectorAll("li");

      var first = elem.querySelectorAll(".lines.first");
      // var second = elem.querySelectorAll(".lines.second");

      const tldelay = i * factor;  
      const tweenduration = 1/13 * factor  // -->  1/cumulated duration of all tweens here * factor

      var smallTL = gsap.timeline()
      smallTL
        .to(".person", {top: '70%', ease: "power1"})

        .from('.person-bubble', {autoAlpha: 0, duration: tweenduration})
        .to('.person-bubble', {autoAlpha: 1, duration: tweenduration})

        .from('.starting-point', 
        {top: '0%', duration: tweenduration, ease:'power2.inOut'})

        .to({}, {duration: tweenduration }) // a little pause in between

        .to('.starting-point', {top: '10%', duration: tweenduration*20, ease:'power2.inOut', autoAlpha: 1}) 

        // .from(first, {xPercent: -100, duration: tweenduration*2, ease:'power2.inOut'}) 

        // .to({}, {duration: tweenduration }) // a little pause in between

        // .to(first, {xPercent: 100, duration: tweenduration*2, ease:'power2.inOut'}) 

        // .to({}, {duration: tweenduration/2 }) // a little pause in between

        // // .from(second, {xPercent: -100, duration: tweenduration*2, ease:'power2.inOut'}) 

        // .to({}, {duration: tweenduration/2 }) // a little pause in between

        // // .to(second, {xPercent: 100, duration: tweenduration*2, ease:'power2.inOut'}) 

        // .to(elem, { autoAlpha: 0, duration: tweenduration })

        // .to({}, {duration: tweenduration}) // a little pause at the end

      ;

      largeTL.add(smallTL, tldelay);
      //largeTL.add(smallTL, tldelay - (tldelay*tweenduration));

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

    // .to('section.end', { autoAlpha: 1, duration: 1 * factor })
    // tl.to(".person", {opacity: 1, ease: "power1", duration: 1})
    // .from(".person-bubble", {opacity: 0, duration: 1 })
    // .fromTo('.starting-point', {opacity: 0, duration:0.5, y:'-20%'}, 
    // {ease: bounceOut, duration: 0.5, y:'100%', opacity: 1});

    // gsap.to('.starting-point', {scale: 0, 
    // scrollTrigger: {
    //   trigger:'.start-animate',
    //   start: 'top top',
    //   pin: true,
    //   toggleActions: "play none none reverse",
    //   end: '+=100',
    //   id: 'starting',
    //   onRefresh:(self) => 
    //     self.progress && self.animation.progress(1)
    // }})

    // gsap.to('.person', {top: '30%', left: '0%', scale: 1.5, 
    // scrollTrigger: {
    //   trigger:'.start-point',
    //   start: '10% top',
    //   toggleActions: "play none none reverse",
    //   end: '+=200',
    //   pin: true,
    // }})
    
    // gsap.to('.talk-bubble', {opacity: 0,
    // scrollTrigger: {
    //   trigger:'.start-point',
    //   start: '10% top',
    //   toggleActions: "play none none reverse",
    //   end: '+=50',
    //   pin: true,
    //   id: 'bubble'
    // }})
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
  <div class="section">
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

    <div class="container py-md-16 d-flex" style="height: 500vh;" id="container">
      <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-top mx-50 align-items-top">
        <div class="col p-0">
        </div>
        <!--/column -->
        <div class="col-lg-7 align-item-center">
          <ul class="progress-list mt-3">
            <!-- <li> -->
              <div class="starting-point">
                <h6 class="display-4 mb-6 pe-xxl-6 fs-64 mb-5">Bhaskara</h6>
                <p class="text-justify fs-30 lh-sm">
                  Seorang ayah muda, hidup dalam kondisi ekonomi yang tidak
                  menguntungkan.
                </p>
              </div>
            <!-- </li> -->
            <li>
              <p class="description fs-18 lh-8">
                <span class="highlight fw-bold">Merawat orangtuanya yang menua</span> telah menguras sumber daya
                finansialnya. Biaya medis yang tak kunjung habis membuatnya merasa
                terjebak dalam utang yang bertambah besar.
              </p>  
            </li>
            <li>
              <p class="description fs-24">
              Selain itu, <span class="highlight fw-bold">biaya
              pendidikan anak-anaknya</span> semakin membuatnya gelisah karena tidak
              tahu bagaimana akan mencukupinya. 
              </p>
            </li>
            <li>
              <p class="description fs-20">
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
          </ul>
          <!-- /.progress-list -->
        </div>
        <!--/column -->
      </div>
      <!--/.row -->
    </div>
    <!-- /.container -->
  </div>
</section>

<!-- /section -->
<FloatNav />

<style>
/* CSS */
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
.starting-point {
  overflow: hidden;
  position: fixed;
  padding-right: 10%;
  width: 60%;
  top: 0%;
  /* left: 40%!important; */
}
div[class*=sec] {
  position: fixed;
  padding-right: 10%;
  /* color: white; */
  padding: 15px;
  border-radius: 10px;
}

.sec-1 {
  width: 20%;
  top: 10% !important;
  left: 30%!important;
  line-height: 25px;
  background: #45C4A0;
}
.sec-2 {
  width: 40%;
  top: 10% !important;
  left: 51%!important;
  background: #FAB757;
  line-height: 25px;
}
.sec-3 {
  width: 40%;
  top: 25% !important;
  left: 51%!important;
  background: #FAB757;
  line-height: 25px;
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
  padding: 6px;
  border-radius: 10px;
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
