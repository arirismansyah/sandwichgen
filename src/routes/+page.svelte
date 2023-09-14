<script>
  import FloatNav from "../components/nav/FloatNav.svelte";
  import { onMount } from "svelte";

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
  <div class="container py-14 py-md-16">
    <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-center">
      <div class="col-lg-7">
        <div class="talk-bubble tri-right round btm-right">
          <div class="talktext">
            <p class="text-center">Hai!, Saya Bhaskara</p>
          </div>
        </div>
        <figure>
          <img
            class="w-auto mt-0"
            src="/images/illustration/people1.svg"
            srcset="/images/illustration/people1.svg"
            alt=""
          />
        </figure>
      </div>
      <!--/column -->
      <div class="col-lg-5">
        <h6 class="display-4 mb-6 pe-xxl-6 fs-24 text-center">
          Bhaskara 
        </h6>
        <p class="text-justify">Seorang ayah muda 
          hidup dalam kondisi ekonomi yang tidak menguntungkan.</p>
        <ul class="progress-list mt-3">
          <li>
            <p class="description">
              Merawat orangtuanya yang menua telah menguras sumber daya finansialnya. Biaya medis yang tak kunjung habis membuatnya merasa terjebak dalam utang yang bertambah besar. 
              Selain itu, biaya pendidikan anak-anaknya semakin membuatnya gelisah karena tidak tahu bagaimana akan mencukupinya. Kondisi ini semakin diperburuk dengan penyesuaian 
              jam kerja yang harus ia lakukan untuk merawat keluarganya. Penghasilannya semakin mengecil, dan ia merasa seperti terperangkap dalam lingkaran yang tak berujung dari 
              masalah keuangan.</p>
            <div class="progressbar line blue" data-value="100" />
          </li>
          <li>
            <p class="description">Namun, kendati terpuruk, Bhaskara tetap berusaha dengan segala cara untuk menjaga keluarganya tetap berjalan. Ia tahu bahwa cinta dan komitmen yang ia miliki terhadap 
              keluarganya adalah kekuatan yang bisa membantu mereka melalui masa-masa sulit ini. Meskipun suasana bisa gelap, ia tetap mencari jalan untuk keluar dan mencari bantuan 
              yang diperlukan untuk mengatasi tantangan ekonominya.</p>
            <div class="progressbar line yellow" data-value="80" />
          </li>
          <li>
            <p class="text-center">
              <b> Tak asing dengan cerita diatas ? </b><br> 
              <b>Pernahkan kalian bertemu dengan Bhaskara lain di sekitar kalian ?</b> <br>
              <b>Atau bahkan, kalian bernasib sama dengan Bhaskara ?. </b></p>
            <div class="progressbar line orange" data-value="85" />
          </li>
          <li>
            <p class="text-center">
              Ya!!. Bhaskara adalah satu dari sekian banyak <br> <span class="hightlight"> generasi sandwich</span> di Indonesia.
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

<style>
/* CSS talk bubble */
.talk-bubble {
	margin: 0px;
  display: inline-block;
  position: relative;
	width: 200px;
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
.tri-right.btm-right:after{
	content: ' ';
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
}
.talktext p{
  /* remove webkit p margins */
  -webkit-margin-before: 0em;
  -webkit-margin-after: 0em;
}
</style>
<!-- content -->
<!-- content -->
