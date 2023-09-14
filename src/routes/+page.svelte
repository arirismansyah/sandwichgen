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
          Bhaskara, seorang ayah muda
          <!-- hidup dalam kondisi ekonomi yang tidak menguntungkan.  -->
        </h6>
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
<!-- content -->
<div class="content-wrapper">
  <!-- /header -->
  <section class="wrapper">
    <!-- /.container -->
    <div class="bg-img-wrapper" style="height: 100vh; overflow: hidden;">
      <img
        style="width: 150%; left: -30%; top: -10%; position: relative;"
        src="/images/illustration/people1.svg"
        alt=""
      />
    </div>
  </section>
  <!-- /section -->

  <!-- /section -->
</div>
<!-- /.content-wrapper -->
<footer class="bg-dark text-inverse">
  <div class="container pt-20 pt-lg-21 pb-7">
    <div class="row gy-6 gy-lg-0">
      <div class="col-lg-4">
        <div class="widget">
          <h3 class="h2 mb-3 text-white">Join the Community</h3>
          <p class="lead mb-5">
            Let's make something great together. We are trusted by over 5000+
            clients. Join them by using our services and grow your business.
          </p>
          <a href="#" class="btn btn-white rounded-pill">Join Us</a>
        </div>
        <!-- /.widget -->
      </div>
      <!-- /column -->
      <div class="col-md-4 col-lg-2 offset-lg-2">
        <div class="widget">
          <h4 class="widget-title text-white mb-3">Need Help?</h4>
          <ul class="list-unstyled text-reset mb-0">
            <li><a href="#">Support</a></li>
            <li><a href="#">Get Started</a></li>
            <li><a href="#">Terms of Use</a></li>
            <li><a href="#">Privacy Policy</a></li>
          </ul>
        </div>
        <!-- /.widget -->
      </div>
      <!-- /column -->
      <div class="col-md-4 col-lg-2">
        <div class="widget">
          <h4 class="widget-title text-white mb-3">Learn More</h4>
          <ul class="list-unstyled mb-0">
            <li><a href="#">About Us</a></li>
            <li><a href="#">Our Story</a></li>
            <li><a href="#">Projects</a></li>
            <li><a href="#">Pricing</a></li>
            <li><a href="#">Features</a></li>
          </ul>
        </div>
        <!-- /.widget -->
      </div>
      <!-- /column -->
      <div class="col-md-4 col-lg-2">
        <div class="widget">
          <h4 class="widget-title text-white mb-3">Get in Touch</h4>
          <address>
            Moonshine St. 14/05 Light City, London, United Kingdom
          </address>
          <a href="mailto:first.last@email.com">info@email.com</a><br /> 00 (123)
          456 78 90
        </div>
        <!-- /.widget -->
      </div>
      <!-- /column -->
    </div>
    <!--/.row -->
    <hr class="mt-13 mt-md-15 mb-7" />
    <div class="d-md-flex align-items-center justify-content-between">
      <p class="mb-2 mb-lg-0">© 2021 Sandbox. All rights reserved.</p>
      <nav class="nav social social-white text-md-end">
        <a href="#"><i class="uil uil-twitter" /></a>
        <a href="#"><i class="uil uil-facebook-f" /></a>
        <a href="#"><i class="uil uil-dribbble" /></a>
        <a href="#"><i class="uil uil-instagram" /></a>
        <a href="#"><i class="uil uil-youtube" /></a>
      </nav>
      <!-- /.social -->
    </div>
    <!-- /div -->
  </div>
  <!-- /.container -->
</footer>
<div class="progress-wrap">
  <svg
    class="progress-circle svg-content"
    width="100%"
    height="100%"
    viewBox="-1 -1 102 102"
  >
    <path d="M50,1 a49,49 0 0,1 0,98 a49,49 0 0,1 0,-98" />
  </svg>
</div>

<!-- content -->

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
  .round {
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
    background: lightgoldenrodyellow;
  }
  /* talk bubble contents */
  .talktext {
    padding: 1em;
    color: whitesmoke;
    text-align: left;
    line-height: 1.5em;
  }
  .talktext p {
    /* remove webkit p margins */
    -webkit-margin-before: 0em;
    -webkit-margin-after: 0em;
  }
</style>
