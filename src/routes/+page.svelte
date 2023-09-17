<script>
  import FloatNav from "../components/nav/FloatNav.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";
  import {ScrollTrigger} from "gsap/dist/ScrollTrigger";
  import {Sound, sound} from 'svelte-sound';
  // import bg_music from '/assets_template/sound.mp3'

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
    //bg sound
    // let sound = new Sound(bg_music);
    // sound.play();

    const tl = gsap.timeline();
    gsap.registerPlugin(ScrollTrigger);
    const factor = 10;

    // gsap.set('.description', { autoAlpha: 0 });
    // gsap.set('.starting-point', { yPercent: -100 });
    gsap.set('.person', { top: '160%' });

    var sections = gsap.utils.toArray(".section");

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

      const tldelay = i * factor;  
      const tweenduration = 1/20 * factor  // -->  1/cumulated duration of all tweens here * factor
      
      var bgTimeline = gsap.timeline()
      bgTimeline
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

        .to({}, {duration: tweenduration });

      largeTL.add(bgTimeline, tldelay);
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
      <!-- <div class="talk-bubble tri-right round btm-right person-bubble">
        <div class="talktext">
          <p class="text-center">Hai!, Saya Bhaskara</p>
        </div>
      </div> -->
    </figure>
    <!-- content sebenarnya -->

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
  /* overscroll-behavior: none; */
  min-height: 100vh;
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
