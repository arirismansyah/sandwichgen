<script>
  import FloatNav from "../components/nav/FloatNav.svelte";
  import TrendChart from "../components/charts/Trend.svelte";
  import PiramidChart from "../components/charts/Piramid.svelte";
  import TPAKChart from "../components/charts/TPAK.svelte";
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
  let count=false;

  onMount(() => {
    loadJS();
    new SplitType('#funfact-title');
    new SplitType("#ina-title");
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
        .to(elem, { autoAlpha: 0, duration: tweenduration/8 })
        .to({}, {duration: tweenduration/2})
      }
      else if (elem.id == "intro-funfact-section") {
        bgTimeline
        .to(elem, { autoAlpha: 1, duration: tweenduration })
        .from(".funfact-bot", {yPercent: 100, ease: "expo", duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .from('#funfact-title .word', {yPercent: -250, stagger: 0.05, delay: 0.05, duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .to("#funfact-title .word", {autoAlpha:0, duration: tweenduration/2})
        .to(".funfact-bot", {yPercent: -100, xPercent: 65, ease: "power1.inOut", scale: 0.4, rotationY: 360, rotationX: 360, duration: tweenduration*4})
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
        .from('.wordcloud-desc p', {xPercent: 110, duration: tweenduration, stagger: 0.05, delay: 0.05})
        .to({}, {duration: tweenduration/2 })
        .to(elem, { autoAlpha: 0, duration: tweenduration/8 })
      } else if (elem.id == 'ina-condition') {
        bgTimeline
        .to(elem, { autoAlpha: 1, duration: tweenduration/2 })
        .from('#ina-title .word', {yPercent: -250, stagger: 0.05, delay: 0.05, duration: tweenduration})
        .from('#people-walk', {xPercent: 110, ease: "expo", duration: tweenduration })
        .from('.question-mark div', {yPercent: 110, ease: "expo", duration: tweenduration })
        .to({}, {duration: tweenduration/2 })
        .to('#ina-title .word', {yPercent: 250, stagger: 0.05, delay: 0.05, duration: tweenduration, onComplete: () => {
          gsap.to('#people-walk', {xPercent: -110, ease: "power1.out", duration: 1 })
          gsap.to('.question-mark div', {yPercent: 110, ease: "expo", duration: 1 })
        }})
        .from('.piramid-chart', {autoAlpha: 0, duration: tweenduration})
        .from('.tpak-chart', {autoAlpha: 0, duration: tweenduration/2, onComplete: () => {
          count++
        }})
        .from('.ina-quote p', {yPercent: -110, duration: tweenduration})
        .from('#people-walk-2', {yPercent: 50, xPercent: 50, duration: tweenduration})
        .to({}, {duration: tweenduration/2 })
        .to(elem, {autoAlpha:0, duration: tweenduration/8})
      } else if (elem.id == 'number-drop-section') {
        bgTimeline
          .from('.number-cont-first .number', {autoAlpha: 0, yPercent: -110, duration: tweenduration*2, onStart: () => {
            let tempTimeline = gsap.timeline();
            // gsap.from('.number-cont-first .number', {
            //   textContent: 20,
            //   duration: 2,
            //   ease: "power1.inOut",
            //   snap: { textContent: 0.01 },
            //   toggleActions: "play pause resume reverse",
            //   stagger: {
            //     each: 1.0,
            //     onUpdate: function() {
            //       this.targets()[0].innerHTML = this.targets()[0].textContent;
            //     },
            //   }
            // })
          }})
          .from('.number-cap:nth-of-type(2)', {autoAlpha: 0, yPercent: -110, duration: tweenduration/2})
          .from('.number-desc:nth-of-type(1)', {autoAlpha: 0, yPercent: -110, duration: tweenduration })
          .to({}, {duration: tweenduration*2 })
          .to('.number-cap:nth-of-type(2)', {autoAlpha: 0, yPercent: 110, duration: tweenduration/2})
          .to('.number-cont-first .number', {autoAlpha: 0, yPercent: 110, duration: tweenduration/2})
          .to('.number-desc:nth-of-type(1)', {autoAlpha: 0, yPercent: 110, duration: tweenduration })
          .to({}, {duration: tweenduration*2 })
          .from('.number-cont-second .number', {autoAlpha: 0, yPercent: -110, duration: tweenduration, onComplete: () => {
            let tempTimeline = gsap.timeline();
            // gsap.from('.number-cont-second .number', {
            //   textContent: 40,
            //   duration: 2,
            //   ease: "power1.inOut",
            //   snap: { textContent: 0.01 },
            //   toggleActions: "play pause resume reverse",
            //   stagger: {
            //     each: 1.0,
            //     onUpdate: function() {
            //       this.targets()[0].innerHTML = this.targets()[0].textContent;
            //     },
            //   }
            // })
          }})
          .from('.number-desc:nth-of-type(2)', {autoAlpha: 0, yPercent: -110, duration: tweenduration })
          .to({}, {duration: tweenduration*2 })
          .to('.number-cont-second .number', {autoAlpha: 0, yPercent: 110, duration: tweenduration/2})
          .to('.number-desc:nth-of-type(2)', {autoAlpha: 0, yPercent: 110, duration: tweenduration })
          .to({}, {duration: tweenduration*2 })
          .from('.number-cont-third .number', {autoAlpha: 0, yPercent: -110, duration: tweenduration, onComplete: () => {
            let tempTimeline = gsap.timeline();
            // gsap.from('.number-cont-third .number', {
            //   textContent: 30,
            //   duration: 2,
            //   ease: "power1.inOut",
            //   snap: { textContent: 0.01 },
            //   toggleActions: "play pause resume reverse",
            //   stagger: {
            //     each: 1.0,
            //     onUpdate: function() {
            //       this.targets()[0].innerHTML = this.targets()[0].textContent;
            //     },
            //   }
            // })
          }})
          .from('.number-desc:nth-of-type(3)', {autoAlpha: 0, yPercent: -110, duration: tweenduration })
          .to({}, {duration: tweenduration*2 })
          .to('.number-cont-third .number', {autoAlpha: 0, yPercent: 110, duration: tweenduration/2})
          .to('.number-desc:nth-of-type(3)', {autoAlpha: 0, yPercent: 110, duration: tweenduration })
          .to({}, {duration: tweenduration*2 })
          .from('.conclusion-number', {autoAlpha: 0, duration: tweenduration})
          .to({}, {duration: tweenduration/2 })
          .to('.conclusion-number', {autoAlpha: 0, duration: tweenduration})
      } else if (elem.id == 'nonoffstat-section') {
        bgTimeline
          .from('#nonoffstat-section .row', {yPercent: -110, autoAlpha: 0, duration: tweenduration, ease: 'power2.inOut'})
          .from('#nonoffstat-conclude', {yPercent: 110, autoAlpha: 0, duration: tweenduration, ease: 'power2.inOut'})
          .to({}, {duration: tweenduration })
          .to('#nonoffstat-section .row', {yPercent: -110, autoAlpha: 0, duration: tweenduration, ease: 'power2.inOut'})
          .to('#nonoffstat-conclude', {yPercent: 110, autoAlpha: 0, duration: tweenduration, ease: 'power2.inOut'})
          
      }


      if (elem.id == 'intro-funfact-section') {
        largeTL.add(bgTimeline, 9.5);
      }
      else if (elem.id == 'ina-condition') {
        largeTL.add(bgTimeline, 16);
      } else if (elem.id == 'number-drop-section') {
        largeTL.add(bgTimeline, 20.5);
      } else if (elem.id == 'nonoffstat-section') {
        largeTL.add(bgTimeline, 31);
      }
      else {
        largeTL.add(bgTimeline, tldelay);
      }
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

    <div class="container py-md-16 d-flex" id="">
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
    </figure>
    <div class="container py-md-16 d-flex" id="">
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
  <!-- generasi sandwhich di ina -->
  <div class="section" id="ina-condition">
    <figure>
      <img
        id="people-walk"
        class="w-auto mt-0 people-walk"
        src="/images/illustration/people_walk.png"
        srcset="/images/illustration/people_walk.png"
        alt=""
      />
      <div class="question-mark">
        <div class="fs-200 fw-bolder q-mark">
          ?
        </div>
      </div>
    </figure>
    <div class="container py-md-16 d-flex">
      <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-top mx-50 align-items-top">
        <div class="col-12 align-item-center">
          <div class="ina-question text-center">
            <p class="fs-56 pt-5 text-center" id="ina-title">
              Lantas, Bagaimana gambaran <b>kondisi penduduknya</b>
            </p>
          </div>
        </div>
      </div>
      <div class="piramid-container row">
        <div class="col-6 piramid-chart">
          <PiramidChart counter={count}/>
        </div>
        <div class="col-6 tpak-chart">
          <TPAKChart counter={count}/>
        </div>
        <div class="col-12 ina-quote">
          <p class="fs-24 text-center fw-bold">
            <svg xmlns="http://www.w3.org/2000/svg" style="margin-bottom: 10px" width="32" height="32" fill="currentColor" class="bi bi-quote" viewBox="0 0 16 16">
              <path d="M12 12a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1h-1.388c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 9 7.558V11a1 1 0 0 0 1 1h2Zm-6 0a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1H4.612c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 3 7.558V11a1 1 0 0 0 1 1h2Z"/>
            </svg>
            Mayoritas penduduk usia pada generasi muda dan tingginya tingginya 
            penduduk bukan angkatan kerja mengindikasikan adanya generasi 
            sandwich di Indonesia.
          </p>
          <figure>
            <img
              id="people-walk-2"
              class="w-auto mt-0 people-walk-2"
              src="/images/illustration/people_walk.png"
              srcset="/images/illustration/people_walk.png"
              alt=""
            />
          </figure>
        </div>
      </div>
    </div>
  </div>

  <!-- number drop -->
  <div class="section" id="number-drop-section">
    <div class="container">
      <div class="row" style="height: 100vh!important">
        <div class="col-6">
          <div class="number-cont">
            <div class="number-cont-first">
              <p class="number fs-150 fw-bolder lh-1">
                44.67
              </p>
              <p class="text-center fs-18 m-0 p-0 number-cap">
                Rasio ketergantungan
              </p>
            </div>
            <div class="number-cont-second">
              <p class="number fs-150 fw-bolder lh-1">
                78.27%
              </p>
              <p class="text-center fs-18 m-0 p-0 number-cap">
                
              </p>
            </div>
            <div class="number-cont-third">
              <p class="number fs-150 fw-bolder lh-1">
                62.64%
              </p>
              <p class="text-center fs-18 m-0 p-0 number-cap">
                
              </p>
            </div>
          </div>
        </div>
        <div class="col-6">
          <div class="desc-cont">
            <p class="number-desc fs-20 me-8">
              Masih ada 44-45 per 100 orang usia non-produktif di Indonesia bergantung kepada mereka yang berusia produktif. (2022)
            </p>
            <p class="number-desc fs-20 me-8">
              Rumah tangga lansia dengan sumber pembiayaan ditopang oleh anggota 
              rumah tangga yang bekerja. (SP2020)
            </p>
            <p class="number-desc fs-20 me-8">
              Penduduk lanjut usia di Indonesia tinggal bersama anak cucunya (Susenas 2017)
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="conclusion-number">
    <div class="fs-32 text-italic text-center font-italic worldbank-quotes">
      <svg xmlns="http://www.w3.org/2000/svg" style="margin-bottom: 10px" width="32" height="32" fill="currentColor" class="bi bi-quote" viewBox="0 0 16 16">
        <path d="M12 12a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1h-1.388c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 9 7.558V11a1 1 0 0 0 1 1h2Zm-6 0a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1H4.612c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 3 7.558V11a1 1 0 0 0 1 1h2Z"/>
      </svg>
      <i><strong>Rasio ketergantungan Indonesia <span class="underline-3 style-2 yellow">lebih tinggi</span> dari beberapa negara Asia lainnya, seperti: Singapura (37), Brunei Darussalam (39), Korea Selatan (41), Malaysia (43)</strong></i>
      <br>Sumber: worldbank      
    </div>
  </div>

  <!-- non-offstat -->
  <div class="section" id="nonoffstat-section">
    <div class="container">
      <div class="row align-item-center" style="height: 100vh!important">
          <div class="col-12 pe-15 my-auto">
            <div class="row nn-1">
              <div class="col-6 nn-number fs-150 fw-bolder lh-1 text-warning">48,7%</div>
              <div class="col-6 text-center my-auto">
                <p class="text-center fs-20 my-auto">
                  Masyarakat produktif Indonesia merupakan generasi sandwich yang memiliki tanggungan finansial atas keluarganya
                </p>
              </div>
            </div>
            <div class="row nn-2">
              <div class="col-6 fs-150 nn-number fw-bolder lh-1 text-success">83,6%</div>
              <div class="col-6 my-auto">
                <p class="text-center fs-20 my-auto">
                  Sandwich Generation di Indonesia percaya kalau mereka mampu merawat tanggungan dengan baik
                </p>
              </div>
            </div>
            <div class="row nn-3">
              <div class="col-6 fs-150 nn-number fw-bolder lh-1 text-danger">13,4%</div>
              <div class="col-6 text-center my-auto">
                <p class="text-center fs-20 my-auto">
                  Sandwich Generation memiliki kesiapan finansial dalam memenuhi kebutuhan pokok, menabung, dan berinvestasi
                </p> 
              </div>
            </div>

            <div class="row mt-7">
              <div class="col-12">

            <div class="fs-28 text-italic text-center" id="nonoffstat-conclude">
              <svg xmlns="http://www.w3.org/2000/svg" style="margin-bottom: 10px" width="32" height="32" fill="currentColor" class="bi bi-quote" viewBox="0 0 16 16">
                <path d="M12 12a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1h-1.388c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 9 7.558V11a1 1 0 0 0 1 1h2Zm-6 0a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1H4.612c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 3 7.558V11a1 1 0 0 0 1 1h2Z"/>
                </svg>
                <i><strong>Hampir <span class="underline-2 style-2 yellow">setengah penduduk produktif</span> Indonesia merupakan Sandwich Generation, 
                  namun tidak banyak yang memiliki kesiapan finansial.
                  </strong></i>
                <br>Sumber: katadata.co.id      
            </div>
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

#nonoffstat-section .nn-1 p{
    color: whitesmoke;
    font-weight: bold;
    background: #FAB757;
    border-radius: 10px;
    padding: 10px;
  }
  #nonoffstat-section .nn-2 p{
    color: whitesmoke;
    font-weight: bold;
    background: #45C3A0;
    border-radius: 10px;
    padding: 10px;
  }
  #nonoffstat-section .nn-3 p{
    color: whitesmoke;
    font-weight: bold;
    background: #E1626B;
    border-radius: 10px;
    padding: 10px;
  }
  .conclusion-number {
    height: 50vh;
    width: 100vw;
    position: fixed;
    top: 30%!important;
    left: 0%;
    padding: 20px;
  }
  .conclusion-number div {
    top: 50%;
    margin: 5%
  }
  /* number container */
.number-cont {
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  height: 100vh;
  padding-right: 20px;
}
.number-cont div {
  overflow: hidden;
  height: fit-content;
  padding-right: 20px;
  position: fixed;
}
.desc-cont {
  display: flex;
  align-items: center;
  overflow: hidden;
  height: 100vh;
  padding-right: 20px;
  padding-right: 75px;
}
.desc-cont p {
  margin-bottom: 0 !important;;
}
.number-desc {
  color: whitesmoke;
  background-color:#FAB757;
  border-radius: 10px;
  text-align: justify;
  padding: 20px;
  margin-right: 100px!important;
  position: fixed;
}

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
  position: relative;
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
.funfact-question, .ina-question {
  position: fixed;
  left: 10%;
  top: 15%;
  width: 80%;
  overflow: hidden;
}
#funfact-title .line, #ina-title .line{
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
/* Word Cloud end */

/* Ina start */
.question-mark {
  position: fixed;
  right: 22%;
  top: 24%;
  height: fit-content;
  transform: rotate(-45deg);
  overflow: hidden;
}

#people-walk, #people-walk-2 {
  position: fixed;
  transform: scale(0.4);
  left: 30%;
  top: -23%;
  z-index: 1;
  -webkit-transform-origin: 50% 50%;
  transform-origin: 50% 50%;
}

#people-walk-2 {
  transform: scale(0.3) rotate(-20deg);
  left: 40%;
  top: 10%;
}

.ina-quote {
  position: absolute;
  bottom: 2%;
  overflow: hidden;
  width: fit-content;
  height: fit-content;
}

.ina-quote p {
  background: #45C3A0;
  color: whitesmoke;
  padding: 10px;
  border-radius: 10px;
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
