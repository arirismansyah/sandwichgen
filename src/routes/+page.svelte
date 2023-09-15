<script>
  import FloatNav from "../components/nav/FloatNav.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";

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
    tl.from(".person", {y:'200%', ease: "power1", duration: 1})
    .from(".person-bubble", {opacity: 0, duration: 1 })
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
      src="/images/illustration/people1.svg"
      srcset="/images/illustration/people1.svg"
      alt=""
    />
    <div class="talk-bubble tri-right round btm-right person-bubble">
      <div class="talktext">
        <p class="text-center">Hai!, Saya Bhaskara</p>
      </div>
    </div>
  </figure>
  <div class="container py-md-16 p-0">
    <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-top">
      <div class="col p-0">
      </div>
      <!--/column -->
      <div class="col-lg-7">
        <div class="starting-point">
          <h6 class="display-4 mb-6 pe-xxl-6 fs-64 mb-5">Bhaskara</h6>
          <p class="text-justify fs-30 lh-sm">
            Seorang ayah muda, hidup dalam kondisi ekonomi yang tidak
            menguntungkan.
          </p>
        </div>
        <ul class="progress-list mt-3">
          <li>
            <p class="description">
              Bhaskara hidup dalam kondisi ekonomi yang tidak menguntungkan,
              merawat orangtuanya yang menua telah menguras sumber daya
              finansialnya. Biaya medis yang tak kunjung habis membuatnya merasa
              terjebak dalam utang yang bertambah besar. Selain itu, biaya
              pendidikan anak-anaknya semakin membuatnya gelisah karena tidak
              tahu bagaimana akan mencukupinya. Kondisi ini semakin diperburuk
              dengan penyesuaian jam kerja yang harus ia lakukan untuk merawat
              keluarganya. Penghasilannya semakin mengecil, dan ia merasa
              seperti terperangkap dalam lingkaran yang tak berujung dari
              masalah keuangan.
            </p>
            <div class="progressbar line blue" data-value="100" />
          </li>
          <li>
            <p class="description">
              Namun, kendati terpuruk, Bhaskara tetap berusaha dengan segala
              cara untuk menjaga keluarganya tetap berjalan. Ia tahu bahwa cinta
              dan komitmen yang ia miliki terhadap keluarganya adalah kekuatan
              yang bisa membantu mereka melalui masa-masa sulit ini. Meskipun
              suasana bisa gelap, ia tetap mencari jalan untuk keluar dan
              mencari bantuan yang diperlukan untuk mengatasi tantangan
              ekonominya.
            </p>
            <div class="progressbar line yellow" data-value="80" />
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
          </li>
          <li>
            <p class="text-center">
              Ya. Mardiansah adalah satu dari sekian banyak <span
                class="hightlight"
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
.person {
  position: fixed;
  bottom: 0%;
  left: 10%;
  transform: scale(2) translate(0, 35%);
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

.hightlight {
  background: #45C4A0;
  color: white;
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
