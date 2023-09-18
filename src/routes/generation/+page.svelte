<script>
  import { onMount } from "svelte";
  import Tpt from "../../components/charts/TPT.svelte";
  import Ipm from "../../components/charts/IPM.svelte";
  import LamaSekolah from "../../components/charts/LamaSekolah.svelte";
  import MelekHuruf from "../../components/charts/MelekHuruf.svelte";
  import HarapanSekolah from "../../components/charts/HarapanSekolah.svelte";
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
  <div class="container pt-14 pt-md-23 pb-14 pb-md-17">
    <div class="row mb-8 text-center">
      <div class="col-lg-8 col-xl-7 mx-auto">
        <h3 class="display-4">Ketergantungan Generasi Tua</h3>
      </div>
      <!-- /column -->
    </div>
    <!-- /.row -->
    <div class="row gx-lg-8 gx-xl-12 gy-10 mb-14 mb-md-17 align-items-center">
      <div class="col-lg-8 position-relative">
        <div
          class="shape bg-dot primary rellax w-17 h-18"
          data-rellax-speed="1"
          style="bottom: -2rem; left: -0.7rem; transform: translate3d(0px, 71px, 0px);"
        />
        <Tpt />
      </div>
      <!--/column -->
      <div class="col-lg-4">
        <p class="mb-5">
          Tingginya tingkat pengangguran, serta rendahnya tingkat pendidikan
          penduduk usia tua mengindikasikan adanya ketergantungan generasi tua
          terhadap generasi selanjutnya.
        </p>
        <div class="row gy-3">
          <ul class="icon-list bullet-bg bullet-soft-leaf mb-0">
            <li>
              Tingkat Pengangguran Terbuka Dari seluruh angkatan kerja, tingkat
              pengangguran pada generasi muda dan generasi tua lebih tinggi dari
              penduduk usia produktif.
            </li>
            <li class="mt-3">
              <p>
                Tingkat Pendidikan Yang Ditamatkan Berdasarkan generasinya,
                mayoritas tingkat pendidikan tertinggi yang ditamatkan generasi
                baby boomer dan generasi X adalah SD dan sederajat.
              </p>
            </li>
          </ul>
        </div>
        <!--/column -->
      </div>
      <!--/column -->
    </div>

    <div class="col-lg-12 mx-auto">
      <h3 class="display-4 mb-0 text-center px-xl-10 px-xxl-15">
        Penduduk Indonesia yang berada di usia produktif sebagai generasi tengah
        bertanggung jawab untuk memutus rantai generasi sandwich. Perbaikan
        kualitas penduduk harus terus dilakukan guna mempersiapkan penduduk yang
        mandiri di usia tua.
      </h3>
      <div
        class="row gx-lg-8 gx-xl-12 process-wrapper text-center mt-9"
        data-cues="slideInUp"
        data-group="process"
        data-disabled="true"
      >
        <!--/column -->

        <!--/column -->
      </div>
      <!--/.row -->
    </div>
    <!--/.row -->
    <div class="row gx-lg-0 gy-10 align-items-center mb-15 mb-lg-18">
      <!--/column -->
      <div class="col-lg-5">
        <h2 class="display-4 mb-3">
          Mampukah Kita Memutus Rantai Generasi Sandwich?
        </h2>
        <p class="lead fs-lg lh-sm">
          Kualitas hidup penduduk usia produktif Indonesia selaku generasi
          tengah yang baik menunjukkan bahwa mereka bersiap menjadi generasi tua
          yang mandiri dan memutus rantai sandwich generation.
        </p>
      </div>
      <div class="col-lg-6">
        <div class="row mb-4">
          <div class="col-6">
            <div class="card shadow-lg">
              <div class="card-body">
                <div class="d-flex d-lg-block d-xl-flex flex-row">
                  <div>
                    <div
                      class="icon btn btn-circle btn-lg btn-soft-purple disabled mx-auto me-4 mb-lg-3 mb-xl-0"
                    >
                      %
                    </div>
                  </div>
                  <div>
                    <h3 class="counter mb-1" style="visibility: visible;">
                      96,35
                    </h3>
                    <p class="mb-0">Angka Melek Huruf</p>
                  </div>
                </div>
              </div>
              <!--/.card-body -->
            </div>
          </div>
          <div class="col-6">
            <div class="card shadow-lg">
              <div class="card-body">
                <div class="d-flex d-lg-block d-xl-flex flex-row">
                  <div>
                    <div
                      class="icon btn btn-circle btn-lg btn-soft-purple disabled mx-auto me-4 mb-lg-3 mb-xl-0"
                    />
                  </div>
                  <div>
                    <h3 class="counter mb-1" style="visibility: visible;">
                      8,69
                    </h3>
                    <p class="mb-0">Rata-Rata Lama Sekolah</p>
                  </div>
                </div>
              </div>
              <!--/.card-body -->
            </div>
          </div>
        </div>
        <div class="row mb-4">
          <div class="col-6">
            <div class="card shadow-lg">
              <div class="card-body">
                <div class="d-flex d-lg-block d-xl-flex flex-row">
                  <div>
                    <div
                      class="icon btn btn-circle btn-lg btn-soft-purple disabled mx-auto me-4 mb-lg-3 mb-xl-0"
                    >
                      <i class="uil uil-presentation-check" />
                    </div>
                  </div>
                  <div>
                    <h3 class="counter mb-1" style="visibility: visible;">
                      72,91
                    </h3>
                    <p class="mb-0">IPM</p>
                  </div>
                </div>
              </div>
              <!--/.card-body -->
            </div>
          </div>
          <div class="col-6">
            <div class="card shadow-lg">
              <div class="card-body">
                <div class="d-flex d-lg-block d-xl-flex flex-row">
                  <div>
                    <div
                      class="icon btn btn-circle btn-lg btn-soft-purple disabled mx-auto me-4 mb-lg-3 mb-xl-0"
                    >
                      <i class="uil uil-presentation-check" />
                    </div>
                  </div>
                  <div>
                    <h3 class="counter mb-1" style="visibility: visible;">
                      13,10
                    </h3>
                    <p class="mb-0">Harapan Lama Sekolah</p>
                  </div>
                </div>
              </div>
              <!--/.card-body -->
            </div>
          </div>
        </div>
        <div class="row mb-4">
          <div class="col">
            <div class="card shadow-lg">
              <div class="card-body">
                <div class="d-flex d-lg-block d-xl-flex flex-row">
                  <div>
                    <div
                      class="icon btn btn-circle btn-lg btn-soft-purple disabled mx-auto me-4 mb-lg-3 mb-xl-0"
                    >
                      <i class="uil uil-presentation-check" />
                    </div>
                  </div>
                  <div>
                    <h3 class="counter mb-1" style="visibility: visible;">
                      75,16
                    </h3>
                    <p class="mb-0">
                      Proporsi Remaja Dan Dewasa Usia 15-59 Tahun Dengan
                      Keterampilan TIK
                    </p>
                  </div>
                </div>
              </div>
              <!--/.card-body -->
            </div>
          </div>
        </div>
      </div>
      <!--/column -->
    </div>

    <div class="row">
      <p class="fs-24">
        Hingga tahun 2022, Indonesia berada pada tren positif perbaikan kualitas
        penduduk, terlihat dari perbaikan berbagai indikator kualitas hidup dan
        indikator pendidikan yang terus tumbuh. Tren positif ini harus terus
        dijaga guna menghasilkan generasi tengah yang mampu mempersiapkan masa
        tua dan memutus rantai generasi sandwich.
      </p>
    </div>
    <!--/.row -->
    <div class="row gx-md-8 gx-xl-10">
      <div class="col-lg-6">
        <div class="card bg-soft-leaf mb-10">
          <div class="card-body p-12">
            <div class="post-category mb-3 text-leaf">
              Rata-rata Lama Sekolah
            </div>

            <LamaSekolah />
          </div>
          <!--/.card-body -->
          <img
            class="card-img-bottom"
            src="./assets/img/photos/f3.png"
            srcset="./assets/img/photos/f3@2x.png 2x"
            alt=""
          />
        </div>
        <!--/.card -->
      </div>
      <!-- /column -->
      <div class="col-lg-6">
        <div class="card bg-soft-pink">
          <div class="card-body p-12">
            <div class="post-category mb-3 text-pink">IPM</div>
            <Ipm />
          </div>
          <!--/.card-body -->
        </div>
        <!--/.card -->
      </div>
      <!-- /column -->
    </div>

    <div class="row gx-md-8 gx-xl-10">
      <div class="col-lg-6">
        <div class="card bg-soft-leaf mb-10">
          <div class="card-body p-12">
            <div class="post-category mb-3 text-leaf">harapan lama sekolah</div>

            <HarapanSekolah />
          </div>
          <!--/.card-body -->
          <img
            class="card-img-bottom"
            src="./assets/img/photos/f3.png"
            srcset="./assets/img/photos/f3@2x.png 2x"
            alt=""
          />
        </div>
        <!--/.card -->
      </div>
      <!-- /column -->
      <div class="col-lg-6">
        <div class="card bg-soft-pink">
          <div class="card-body p-12">
            <div class="post-category mb-3 text-pink">Angka melek huruf</div>
            <MelekHuruf />
          </div>
          <!--/.card-body -->
          <img
            class="card-img-bottom"
            src="./assets/img/photos/f4.png"
            srcset="./assets/img/photos/f4@2x.png 2x"
            alt=""
          />
        </div>
        <!--/.card -->
      </div>
      <!-- /column -->
    </div>

    <div
      class="col-lg-12 text-center mx-auto"
      data-cues="zoomIn"
      data-group="welcome"
      data-interval="-200"
      data-disabled="true"
    >
      <p
        class="lead fs-24 lh-sm px-md-5 px-xl-15 px-xxl-10 mb-7"
        data-cue="zoomIn"
        data-interval="-200"
        data-group="welcome"
        data-show="true"
        style="animation-name: zoomIn; animation-duration: 700ms; animation-timing-function: ease; animation-delay: 500ms; animation-direction: normal; animation-fill-mode: both;"
      >
        Generasi penerus memang bukanlah mereka yang sedang memegang kekuasaan,
        bukan mereka yang mendorong perekonomian Indonesia saat ini. Akan tetapi
        nanti, saat ulang tahun ke-100 kemerdekaan RI, mereka lah para pemimpin
        dan penggerak perekonomian Indonesia. Perbaikan kualitas para generasi
        penerus merupakan suatu prioritas guna mewujudkan Indonesia Emas 2045.
      </p>
    </div>
  </div>

  <!-- /.container -->
</section>
