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
  <section class="wrapper bg-gray">
    <!-- /.container -->
    <figure style="bottom: 80%; left: -100%; z-index: 2;">
      <img style="left: -50%;" src="/images/illustration/people1.svg" alt="" />
    </figure>
  </section>
  <!-- /section -->
  <section class="wrapper bg-gray">
    <div class="container">
      <div class="card shadow-none my-n13 my-md-n15 my-lg-n17">
        <div class="card-body py-12 py-lg-14 px-lg-11 py-xl-16 px-xl-13">
          <div class="row text-center">
            <div class="col-lg-9 col-xl-8 col-xxl-7 mx-auto">
              <h2 class="fs-15 text-uppercase text-muted mb-3">What We Do?</h2>
              <h3 class="display-4 mb-9">
                The service we offer is specifically designed to meet your
                needs.
              </h3>
            </div>
            <!-- /column -->
          </div>
          <!-- /.row -->
          <div class="row gx-md-8 gx-xl-12 gy-8 mb-14 mb-md-16 text-center">
            <div class="col-md-4">
              <div
                class="icon btn btn-block btn-lg btn-soft-purple disabled mb-5"
              >
                <i class="uil uil-phone-volume" />
              </div>
              <h4>24/7 Support</h4>
              <p class="mb-3">
                Fusce dapibus tellus cursus porta tortor condimentum euismod
                massa justo vehicula sit amet et risus cras.
              </p>
              <a href="#" class="more hover link-purple">Learn More</a>
            </div>
            <!--/column -->
            <div class="col-md-4">
              <div
                class="icon btn btn-block btn-lg btn-soft-green disabled mb-5"
              >
                <i class="uil uil-shield-exclamation" />
              </div>
              <h4>Secure Payments</h4>
              <p class="mb-3">
                Fusce dapibus tellus cursus porta tortor condimentum euismod
                massa justo vehicula sit amet et risus cras.
              </p>
              <a href="#" class="more hover link-green">Learn More</a>
            </div>
            <!--/column -->
            <div class="col-md-4">
              <div
                class="icon btn btn-block btn-lg btn-soft-orange disabled mb-5"
              >
                <i class="uil uil-laptop-cloud" />
              </div>
              <h4>Daily Updates</h4>
              <p class="mb-3">
                Fusce dapibus tellus cursus porta tortor condimentum euismod
                massa justo vehicula sit amet et risus cras.
              </p>
              <a href="#" class="more hover link-orange">Learn More</a>
            </div>
            <!--/column -->
          </div>
          <!--/.row -->
          <div class="row gx-md-8 gx-xl-12 gy-10 align-items-center">
            <div class="col-lg-6">
              <h2 class="fs-15 text-uppercase text-muted mb-3">Our Strategy</h2>
              <h3 class="display-4 mb-5">
                3 working steps to organize our business projects.
              </h3>
              <p>
                Aenean eu leo quam. Pellentesque ornare sem lacinia quam
                venenatis vestibulum. Etiam porta sem malesuada magna mollis
                euismod eget. Nullam id dolor id nibh ultricies vehicula ut id
                elit. Nullam quis risus.
              </p>
              <p class="mb-6">
                Nullam id dolor id nibh ultricies vehicula ut id elit.
                Vestibulum id ligula porta felis euismod semper. Aenean lacinia
                bibendum consectetur.
              </p>
              <a href="#" class="btn btn-primary rounded-pill mb-0"
                >Learn More</a
              >
            </div>
            <!--/column -->
            <div class="col-lg-6">
              <div class="d-flex flex-row">
                <div>
                  <span
                    class="icon btn btn-block btn-lg btn-soft-purple disabled mt-1 me-5"
                    ><span class="number fs-22">01</span></span
                  >
                </div>
                <div>
                  <h4 class="mb-1">Collect Ideas</h4>
                  <p class="mb-0">
                    Nulla vitae elit libero pharetra augue dapibus. Fusce
                    dapibus, tellus ac cursus commodo.
                  </p>
                </div>
              </div>
              <div class="d-flex flex-row mt-8 ms-lg-10">
                <div>
                  <span
                    class="icon btn btn-block btn-lg btn-soft-green disabled mt-1 me-5"
                    ><span class="number fs-22">02</span></span
                  >
                </div>
                <div>
                  <h4 class="mb-1">Data Analysis</h4>
                  <p class="mb-0">
                    Vivamus sagittis lacus vel augue laoreet tortor mauris
                    condimentum fermentum.
                  </p>
                </div>
              </div>
              <div class="d-flex flex-row mt-8">
                <div>
                  <span
                    class="icon btn btn-block btn-lg btn-soft-orange disabled mt-1 me-5"
                    ><span class="number fs-22">03</span></span
                  >
                </div>
                <div>
                  <h4 class="mb-1">Finalize Product</h4>
                  <p class="mb-0">
                    Cras mattis consectetur purus sit amet massa justo sit amet
                    risus consectetur magna elit.
                  </p>
                </div>
              </div>
            </div>
            <!--/column -->
          </div>
          <!--/.row -->
          <hr class="my-14 my-md-16" />
          <div class="row gx-lg-8 gx-xl-12 gy-10 gy-lg-0 mb-11 align-items-end">
            <div class="col-lg-4">
              <h2 class="fs-15 text-uppercase text-muted mb-3">
                Company Facts
              </h2>
              <h3 class="display-4 mb-0">We are proud of our works</h3>
            </div>
            <!-- /column -->
            <div class="col-lg-8 mt-lg-2">
              <div
                class="row align-items-center counter-wrapper gy-6 text-center"
              >
                <div class="col-md-4">
                  <h3 class="counter counter-lg">1000+</h3>
                  <p>Completed Projects</p>
                </div>
                <!--/column -->
                <div class="col-md-4">
                  <h3 class="counter counter-lg">500+</h3>
                  <p>Happy Clients</p>
                </div>
                <!--/column -->
                <div class="col-md-4">
                  <h3 class="counter counter-lg">150+</h3>
                  <p>Awards Won</p>
                </div>
                <!--/column -->
              </div>
              <!--/.row -->
            </div>
            <!-- /column -->
          </div>
          <!-- /.row -->
          <div class="card bg-gray shadow-lg mb-14 mb-md-17">
            <div class="row gx-0">
              <div
                class="col-lg-6 image-wrapper bg-image bg-cover rounded-top rounded-lg-start"
                data-image-src="/assets_template/img/photos/tm1.jpg"
              />
              <!--/column -->
              <div class="col-lg-6">
                <div class="p-10 p-xl-13">
                  <div
                    class="swiper-container dots-closer mb-6"
                    data-margin="30"
                    data-dots="true"
                  >
                    <div class="swiper">
                      <div class="swiper-wrapper">
                        <div class="swiper-slide">
                          <blockquote class="icon icon-top fs-lg text-center">
                            <p>
                              “Vivamus sagittis lacus vel augue laoreet rutrum
                              faucibus dolor auctor. Vestibulum ligula porta
                              felis euismod semper.”
                            </p>
                            <div
                              class="blockquote-details justify-content-center text-center"
                            >
                              <div class="info ps-0">
                                <h5 class="mb-1">Coriss Ambady</h5>
                                <p class="mb-0">Financial Analyst</p>
                              </div>
                            </div>
                          </blockquote>
                        </div>
                        <!--/.swiper-slide -->
                        <div class="swiper-slide">
                          <blockquote class="icon icon-top fs-lg text-center">
                            <p>
                              “Vivamus sagittis lacus vel augue laoreet rutrum
                              faucibus dolor auctor. Vestibulum ligula porta
                              felis euismod semper.”
                            </p>
                            <div
                              class="blockquote-details justify-content-center text-center"
                            >
                              <div class="info ps-0">
                                <h5 class="mb-1">Cory Zamora</h5>
                                <p class="mb-0">Marketing Specialist</p>
                              </div>
                            </div>
                          </blockquote>
                        </div>
                        <!--/.swiper-slide -->
                        <div class="swiper-slide">
                          <blockquote class="icon icon-top fs-lg text-center">
                            <p>
                              “Vivamus sagittis lacus vel augue laoreet rutrum
                              faucibus dolor auctor. Vestibulum ligula porta
                              felis euismod semper.”
                            </p>
                            <div
                              class="blockquote-details justify-content-center text-center"
                            >
                              <div class="info ps-0">
                                <h5 class="mb-1">Nikolas Brooten</h5>
                                <p class="mb-0">Sales Manager</p>
                              </div>
                            </div>
                          </blockquote>
                        </div>
                        <!--/.swiper-slide -->
                      </div>
                      <!--/.swiper-wrapper -->
                    </div>
                    <!-- /.swiper -->
                  </div>
                  <!-- /.swiper-container -->
                </div>
                <!--/div -->
              </div>
              <!--/column -->
            </div>
            <!--/.row -->
          </div>
          <!-- /.card -->
          <div class="row text-center">
            <div class="col-lg-10 col-xl-10 col-xxl-8 mx-auto">
              <h2 class="fs-15 text-uppercase text-muted mb-3">Case Studies</h2>
              <h3 class="display-4 mb-9">
                Check out some of our awesome projects with creative ideas and
                great design.
              </h3>
            </div>
            <!-- /column -->
          </div>
          <!-- /.row -->
          <div
            class="swiper-container blog grid-view mb-18"
            data-margin="30"
            data-dots="true"
            data-items-xl="3"
            data-items-md="2"
            data-items-xs="1"
          >
            <div class="swiper">
              <div class="swiper-wrapper">
                <div class="swiper-slide">
                  <article>
                    <figure class="overlay overlay-1 hover-scale rounded mb-6">
                      <a href="#">
                        <img
                          src="/assets_template/img/photos/b4.jpg"
                          alt=""
                        /></a
                      >
                      <figcaption>
                        <h5 class="from-top mb-0">Read More</h5>
                      </figcaption>
                    </figure>
                    <div class="post-header">
                      <h2 class="post-title h3 mb-3">
                        <a class="link-dark" href="./blog-post.html"
                          >Ligula tristique quis risus</a
                        >
                      </h2>
                    </div>
                    <!-- /.post-header -->
                    <div class="post-footer">
                      <ul class="post-meta">
                        <li class="post-date">
                          <i class="uil uil-calendar-alt" /><span
                            >14 Apr 2021</span
                          >
                        </li>
                        <li class="post-comments">
                          <a href="#"
                            ><i class="uil uil-file-alt fs-15" />Coding</a
                          >
                        </li>
                      </ul>
                      <!-- /.post-meta -->
                    </div>
                    <!-- /.post-footer -->
                  </article>
                  <!-- /article -->
                </div>
                <!--/.swiper-slide -->
                <div class="swiper-slide">
                  <article>
                    <figure class="overlay overlay-1 hover-scale rounded mb-6">
                      <a href="#">
                        <img
                          src="/assets_template/img/photos/b5.jpg"
                          alt=""
                        /></a
                      >
                      <figcaption>
                        <h5 class="from-top mb-0">Read More</h5>
                      </figcaption>
                    </figure>
                    <div class="post-header">
                      <h2 class="post-title h3 mb-3">
                        <a class="link-dark" href="./blog-post.html"
                          >Nullam id dolor elit id nibh</a
                        >
                      </h2>
                    </div>
                    <!-- /.post-header -->
                    <div class="post-footer">
                      <ul class="post-meta">
                        <li class="post-date">
                          <i class="uil uil-calendar-alt" /><span
                            >29 Mar 2021</span
                          >
                        </li>
                        <li class="post-comments">
                          <a href="#"
                            ><i class="uil uil-file-alt fs-15" />Workspace</a
                          >
                        </li>
                      </ul>
                      <!-- /.post-meta -->
                    </div>
                    <!-- /.post-footer -->
                  </article>
                  <!-- /article -->
                </div>
                <!--/.swiper-slide -->
                <div class="swiper-slide">
                  <article>
                    <figure class="overlay overlay-1 hover-scale rounded mb-6">
                      <a href="#">
                        <img
                          src="/assets_template/img/photos/b6.jpg"
                          alt=""
                        /></a
                      >
                      <figcaption>
                        <h5 class="from-top mb-0">Read More</h5>
                      </figcaption>
                    </figure>
                    <div class="post-header">
                      <h2 class="post-title h3 mb-3">
                        <a class="link-dark" href="./blog-post.html"
                          >Ultricies fusce porta elit</a
                        >
                      </h2>
                    </div>
                    <!-- /.post-header -->
                    <div class="post-footer">
                      <ul class="post-meta">
                        <li class="post-date">
                          <i class="uil uil-calendar-alt" /><span
                            >26 Feb 2021</span
                          >
                        </li>
                        <li class="post-comments">
                          <a href="#"
                            ><i class="uil uil-file-alt fs-15" />Meeting</a
                          >
                        </li>
                      </ul>
                      <!-- /.post-meta -->
                    </div>
                    <!-- /.post-footer -->
                  </article>
                  <!-- /article -->
                </div>
                <!--/.swiper-slide -->
                <div class="swiper-slide">
                  <article>
                    <figure class="overlay overlay-1 hover-scale rounded mb-6">
                      <a href="#">
                        <img
                          src="/assets_template/img/photos/b7.jpg"
                          alt=""
                        /></a
                      >
                      <figcaption>
                        <h5 class="from-top mb-0">Read More</h5>
                      </figcaption>
                    </figure>
                    <div class="post-header">
                      <h2 class="post-title h3 mb-3">
                        <a class="link-dark" href="./blog-post.html"
                          >Morbi leo risus porta eget</a
                        >
                      </h2>
                    </div>
                    <div class="post-footer">
                      <ul class="post-meta">
                        <li class="post-date">
                          <i class="uil uil-calendar-alt" /><span
                            >7 Jan 2021</span
                          >
                        </li>
                        <li class="post-comments">
                          <a href="#"
                            ><i class="uil uil-file-alt fs-15" />Business Tips</a
                          >
                        </li>
                      </ul>
                      <!-- /.post-meta -->
                    </div>
                    <!-- /.post-footer -->
                  </article>
                  <!-- /article -->
                </div>
                <!--/.swiper-slide -->
              </div>
              <!--/.swiper-wrapper -->
            </div>
            <!-- /.swiper -->
          </div>
          <!-- /.swiper-container -->
          <hr class="my-14 my-md-16" />
          <div
            class="row gx-lg-8 gx-xl-12 gy-10 mb-14 mb-md-17 align-items-center"
          >
            <div class="col-md-8 col-lg-6 order-lg-2">
              <figure class="rounded">
                <img
                  src="/assets_template/img/photos/about24.jpg"
                  srcset="/assets_template/img/photos/about24@2x.jpg 2x"
                  alt=""
                />
              </figure>
            </div>
            <!--/column -->
            <div class="col-lg-6">
              <h2 class="fs-15 text-uppercase text-muted mb-3">Our Team</h2>
              <h3 class="display-4 mb-5">
                Save your time by choosing our professional team.
              </h3>
              <p class="mb-6">
                Cum sociis natoque penatibus et magnis dis parturient montes,
                nascetur ridiculus mus. Cras justo odio, dapibus ac facilisis
                in, egestas eget quam. Praesent commodo cursus magna, vel
                scelerisque nisl consectetur et.
              </p>
              <div class="row gy-3 gx-xl-8">
                <div class="col-xl-6">
                  <ul class="icon-list bullet-bg bullet-soft-primary mb-0">
                    <li>
                      <span><i class="uil uil-check" /></span><span
                        >Aenean eu leo quam ornare curabitur blandit tempus.</span
                      >
                    </li>
                    <li class="mt-3">
                      <span><i class="uil uil-check" /></span><span
                        >Nullam quis risus eget urna mollis ornare donec elit.</span
                      >
                    </li>
                  </ul>
                </div>
                <!--/column -->
                <div class="col-xl-6">
                  <ul class="icon-list bullet-bg bullet-soft-primary mb-0">
                    <li>
                      <span><i class="uil uil-check" /></span><span
                        >Etiam porta sem malesuada magna mollis euismod.</span
                      >
                    </li>
                    <li class="mt-3">
                      <span><i class="uil uil-check" /></span><span
                        >Fermentum massa vivamus faucibus amet euismod.</span
                      >
                    </li>
                  </ul>
                </div>
                <!--/column -->
              </div>
              <!--/.row -->
            </div>
            <!--/column -->
          </div>
          <!--/.row -->
          <div
            class="row gy-10 gx-lg-8 gx-xl-12 mb-14 mb-md-16 align-items-center"
          >
            <div class="col-md-8 col-lg-6">
              <figure class="rounded">
                <img
                  src="/assets_template/img/photos/about25.jpg"
                  srcset="/assets_template/img/photos/about25@2x.jpg 2x"
                  alt=""
                />
              </figure>
            </div>
            <!--/column -->
            <div class="col-lg-6">
              <h2 class="fs-15 text-uppercase text-muted mb-3">
                Why Choose Us?
              </h2>
              <h3 class="display-4 mb-7">
                A few reasons why our valued customers choose us.
              </h3>
              <div class="accordion accordion-wrapper" id="accordionExample">
                <div class="card plain accordion-item">
                  <div class="card-header" id="headingOne">
                    <button
                      class="accordion-button"
                      data-bs-toggle="collapse"
                      data-bs-target="#collapseOne"
                      aria-expanded="true"
                      aria-controls="collapseOne"
                    >
                      Professional Design
                    </button>
                  </div>
                  <!--/.card-header -->
                  <div
                    id="collapseOne"
                    class="accordion-collapse collapse show"
                    aria-labelledby="headingOne"
                    data-bs-parent="#accordionExample"
                  >
                    <div class="card-body">
                      <p>
                        Fusce dapibus, tellus ac cursus commodo, tortor mauris
                        condimentum nibh, ut fermentum massa justo sit amet
                        risus. Cras mattis consectetur purus sit amet fermentum.
                        Praesent commodo cursus magna, vel.
                      </p>
                    </div>
                    <!--/.card-body -->
                  </div>
                  <!--/.accordion-collapse -->
                </div>
                <!--/.accordion-item -->
                <div class="card plain accordion-item">
                  <div class="card-header" id="headingTwo">
                    <button
                      class="collapsed"
                      data-bs-toggle="collapse"
                      data-bs-target="#collapseTwo"
                      aria-expanded="false"
                      aria-controls="collapseTwo"
                    >
                      Top-Notch Support
                    </button>
                  </div>
                  <!--/.card-header -->
                  <div
                    id="collapseTwo"
                    class="accordion-collapse collapse"
                    aria-labelledby="headingTwo"
                    data-bs-parent="#accordionExample"
                  >
                    <div class="card-body">
                      <p>
                        Fusce dapibus, tellus ac cursus commodo, tortor mauris
                        condimentum nibh, ut fermentum massa justo sit amet
                        risus. Cras mattis consectetur purus sit amet fermentum.
                        Praesent commodo cursus magna, vel.
                      </p>
                    </div>
                    <!--/.card-body -->
                  </div>
                  <!--/.accordion-collapse -->
                </div>
                <!--/.accordion-item -->
                <div class="card plain accordion-item">
                  <div class="card-header" id="headingThree">
                    <button
                      class="collapsed"
                      data-bs-toggle="collapse"
                      data-bs-target="#collapseThree"
                      aria-expanded="false"
                      aria-controls="collapseThree"
                    >
                      Header and Slider Options
                    </button>
                  </div>
                  <!--/.card-header -->
                  <div
                    id="collapseThree"
                    class="accordion-collapse collapse"
                    aria-labelledby="headingThree"
                    data-bs-parent="#accordionExample"
                  >
                    <div class="card-body">
                      <p>
                        Fusce dapibus, tellus ac cursus commodo, tortor mauris
                        condimentum nibh, ut fermentum massa justo sit amet
                        risus. Cras mattis consectetur purus sit amet fermentum.
                        Praesent commodo cursus magna, vel.
                      </p>
                    </div>
                    <!--/.card-body -->
                  </div>
                  <!--/.accordion-collapse -->
                </div>
                <!--/.accordion-item -->
              </div>
              <!--/.accordion -->
            </div>
            <!--/column -->
          </div>
          <!--/.row -->
          <div
            class="wrapper image-wrapper bg-auto no-overlay bg-image text-center bg-map"
            data-image-src="/assets_template/img/map.png"
          >
            <div class="container py-md-16 py-lg-18">
              <div class="row">
                <div class="col-xl-11 col-xxl-9 mx-auto">
                  <h3 class="display-4 mb-8 px-lg-8">
                    We are trusted by over 5000+ clients. Join them now and grow
                    your business.
                  </h3>
                </div>
                <!-- /column -->
              </div>
              <!-- /.row -->
              <div class="d-flex justify-content-center">
                <span
                  ><a class="btn btn-primary rounded-pill">Get Started</a></span
                >
              </div>
            </div>
            <!-- /.container -->
          </div>
          <!-- /.wrapper -->
        </div>
        <!--/.card-body -->
      </div>
      <!--/.card -->
    </div>
    <!-- /.container -->
  </section>
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
