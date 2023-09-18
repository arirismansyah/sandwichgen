<script>
  // import components
  import Backgroud from "./../../components/intro/Backgroud.svelte";
  import FloatNav from "./../../components/nav/FloatNav.svelte";

  // import svelte
  import { onMount } from "svelte";
  import Saos from "saos";
  import { bounceOut, sineOut } from "svelte/easing";
  import { fly } from "svelte/transition";

  //   import gsap
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import { fade, scale } from "svelte/transition";
  import { warning } from "framer-motion";

  // theme js
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
    // load js theme
    loadJS();

    // gsap start
    gsap.registerPlugin(ScrollTrigger);
    const tl_0 = gsap.timeline({
      scrollTrigger: {
        trigger: ".animate-sec1",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart none none reverse",
      },
    });

    const tl_1 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec1",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_2 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec2",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_3 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec3",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_4 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec4",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_5 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec5",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart none reverse reverse",
      },
    });

    const tl_6 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec5",
        start: "top bottom",
        end: "bottom center",
        toggleActions: "restart reverse complete reverse",
      },
    });

    tl_0.fromTo(
      ".content-bg1",
      { opacity: 0, duration: 0.5, y: "-20%" },
      {
        ease: sineOut,
        duration: 0.5,
        y: "0",
        position: "fixed",
        opacity: 1,
      }
    );

    tl_5.fromTo(
      ".content-bg1",
      {
        ease: sineOut,
        opacity: 0,
        duration: 0.5,
        y: "-20%",
      },
      {
        ease: sineOut,
        opacity: 1,
        duration: 0.5,
        y: "100%",
      }
    );

    tl_1
      .to("#sec1", { position: "fixed", top: 0, y: 0 })
      .fromTo(
        ".sec1-elem1",
        { opacity: 0, duration: 0.5, y: "-20%" },
        { duration: 0.5, y: "100%", opacity: 1 }
      )
      .fromTo(
        ".sec1-elem2",
        { opacity: 0, duration: 0.5, y: "-20%" },
        { duration: 0.5, y: "100%", opacity: 1 }
      );

    tl_2
      .to("#sec2", { position: "fixed", top: 0, y: 0 })
      .fromTo(
        ".sec2-elem1",
        { opacity: 0, duration: 0.2, y: "-20%" },
        { ease: sineOut, duration: 0.5, y: "100%", opacity: 1 }
      )
      .fromTo(
        ".sec2-elem2",
        { opacity: 0, duration: 0.5, y: "-20%" },
        { ease: sineOut, duration: 0.5, y: "100%", opacity: 1 }
      );

    tl_3
      .to("#sec3", { position: "fixed", top: 0, y: 0 })
      .fromTo(
        ".sec3-elem1",
        { opacity: 0, duration: 0.2 },
        { duration: 0.5, opacity: 1 }
      )
      .fromTo(
        ".sec3-elem2",
        { opacity: 0, duration: 0.5 },
        { duration: 0.5, opacity: 1 }
      );

    tl_4
      .to("#sec4", { position: "fixed", top: 0, y: 0 })
      .fromTo(
        ".sec4-elem1",
        { opacity: 0, duration: 0.5 },
        { duration: 0.5, opacity: 1 }
      );
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

<div class="wrapper">
  <!-- pre section -->
  <section id="sce0" class="content container d-flex align-items-center">
    <div class="col">
      <figure class="content-bg1 bg-image-1 bg-overlay bg-overlay-300">
        <img src="/images/illustration/people2.png" alt="" />
      </figure>
    </div>
  </section>

  <section id="sec1" class="content d-flex align-items-center">
    <div class="col">
      <!-- row 1 -->
      <div class="row m-4">
        <div class="col-md-12">
          <div class="animate-sec1" />
          <h2 class="fs-32 mb-3 sec1-elem1 text-muted">Lantas</h2>
          <div class="sec1-elem2">
            <h2 class="display-3 mb-10 style-2 yellow">
              Apa itu Generasi <span
                class="underline-3 style-2 yellow sec1-elem3">Sandwich?</span
              >
            </h2>
          </div>
        </div>
      </div>
    </div>
    <!-- background -->
  </section>

  <section id="sec2" class="content container d-flex align-items-center">
    <div class="row m-4">
      <div class="col-md-12">
        <div class="animate-sec2" />
        <h2 class="fs-32 mb-3 sec2-elem1 text-muted">Mengapa</h2>
        <div class="sec2-elem2">
          <h2 class="display-3 mb-10 style-2 yellow">
            disebut Generasi <span class="underline-3 style-2 yellow sec2-elem3"
              >Sandwich?</span
            >
          </h2>
        </div>
      </div>
    </div>
  </section>

  <section id="sec3" class="content container d-flex align-items-center">
    <div class="row m-4">
      <div class="col-md-12">
        <div class="animate-sec3" />
        <h2 class="fs-32 mb-3 sec3-elem1 text-muted">dan bagaimana</h2>
        <div class="sec3-elem2">
          <h2 class="display-3 mb-3 style-2 yellow">
            Bhaskara <span class="underline-3 style-2 yellow sec3-elem3"
              >dapat keluar</span
            >
          </h2>
          <h2 class="fs-32 mb-3 sec3-elem1 text-muted">
            dari jerat ekonomi yang begitu sulit?
          </h2>
        </div>
      </div>
    </div>
  </section>

  <section id="sec4" class="content container d-flex align-items-center">
    <div class="row m-4">
      <div class="col-md-12">
        <div class="animate-sec4" />
        <div class="sec4-elem1">
          <h2 class="display-3 mb-3 style-2 yellow">Mari kita simak ...</h2>
        </div>
      </div>
    </div>
  </section>

  <!-- definisi -->
  <section id="sec5" class="content container d-flex align-items-center">
    <div class="col animate-sec5">
      <div class="row m-4">
        <div class="col-md-12">
          <!-- definisi -->

          <div class="row text-left">
            <div class="card bg-soft-primary card-border-start border-primary">
              <div class="card-body">
                <div class="row text-left">
                  <h3 class="display-2 mb-4">Generasi Sandwich</h3>
                </div>
                <p>
                  merupakan generasi orang dewasa yang harus menanggung hidup 3
                  generasi yaitu orang tuanya, diri sendiri, dan anaknya.
                </p>
              </div>
            </div>
          </div>

          <!-- definisi -->
        </div>
      </div>
      <div class="row m-4">
        <div class="col-md-4">
          <!-- image bhaskara -->
          <figure class="content-illust1 bg-overlay bg-overlay-300">
            <img src="/images/illustration/people1.png" alt="" />
          </figure>
          <!-- image bhaskara -->
        </div>
        <div class="col-md-8 d-flex align-items-center">
          <!-- avatar -->
          <div
            class="row d-flex justify-content-around align-items-center counter-wrapper gy-6 text-center"
          >
            <div class="col-sm-3">
              <div class="card">
                <div class="card-body col shadow-lg text-center">
                  <div class="row d-flex justify-content-center">
                    <img src="/images/illustration/avatar_elder_1.png" alt="" />
                  </div>
                  <div class="row d-flex justify-content-center">
                    <p class="mb-0">Orang Tua</p>
                  </div>
                </div>
              </div>
            </div>
            <!--/column -->
            <div class="col-sm-3">
              <div class="card">
                <div class="card-body col shadow-lg text-center">
                  <div class="row d-flex justify-content-center">
                    <img
                      src="/images/illustration/avatar_middle_1.png"
                      alt=""
                      style="height: 80%;"
                    />
                  </div>
                  <div class="row d-flex justify-content-center">
                    <p class="mb-0">Diri Sendiri</p>
                  </div>
                </div>
              </div>
            </div>
            <!--/column -->
            <div class="col-sm-3">
              <div class="card">
                <div class="card-body col shadow-lg text-center">
                  <div class="row d-flex justify-content-center">
                    <img src="/images/illustration/avatar_kid_1.png" alt="" />
                  </div>
                  <div class="row d-flex justify-content-center">
                    <p class="mb-0">Anak</p>
                  </div>
                </div>
              </div>
            </div>
            <!--/column -->
          </div>
          <!-- avatar -->
        </div>
      </div>
    </div>
  </section>
  <!-- definisi -->

  <section id="sec6" class="content container d-flex align-items-center">
    <div class="row">
      <div class="col-lg-6">
        <img
          class="img-fluid"
          src="/images/illustration/people_sandwich_illustration.png"
          srcset="/images/illustration/people_sandwich_illustration.png 1x"
          alt=""
        />
      </div>
      <div class="col-lg-6 d-flex align-items-center ml-4">
        <div class="row">
          <div class="col-md-10">
            <h3 class="fs-28 m-4">Generasi Sandwich</h3>

            <div class="card shadow-lg me-lg-6 m-4">
              <div class="card-body">
                <p>
                  Mereka berada di tengah-tengah, seperti "terjepit" di antara
                  dua tanggung jawab perawatan yang berbeda.
                </p>
              </div>
            </div>

            <div class="card shadow-lg me-lg-6 m-4">
              <div class="card-body">
                <p>
                  Mirip dengan sebuah "sandwich" yang memiliki dua generasi yang
                  memerlukan perhatian dan dukungan.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="sec7" class="content container d-flex align-items-center">
    <div class="col">
      <figure class="content-bg2 bg-image-2 bg-overlay bg-overlay-300">
        <img src="/images/illustration/elder1.png" alt="" />
      </figure>
    </div>
  </section>

  <section id="sec8" class="content container d-flex align-items-center">
    <div class="row d-flex justify-content-end">
      <div class="col-8">
        <div class="row m-4">
          <div class="col-md-12">
            <div class="animate-sec8 row">
              <div class="sec8-elem2">
                <h2 class="display-5 mb-3 style-2 yellow">
                  Kegagalan <span class="underline-3 style-2 yellow sec8-elem3"
                    >finansial</span
                  > orang tua
                </h2>
                <h2 class="fs-24 mb-3 text-muted">
                  yang tidak memiliki perencanaan finansial untuk masa tuanya
                </h2>
              </div>

              <div class="sec8-elem2">
                <h2 class="fs-24 mb-3 text-muted">
                  akan berpotensi besar membuat sang anak menjadi
                </h2>
                <h2 class="display-5 mb-3 style-2 yellow">
                  Generasi Sandwich berikutnya.
                </h2>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <FloatNav />
</div>

<style>
  .content {
    height: 100vh;
    left: 15vh;
  }

  .bg-image-1 {
    top: 10%;
    left: 55%;
    transform: scale(0.95);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    z-index: -1;
  }

  .bg-image-2 {
    position: fixed;
    top: 10%;
    right: 55%;
    transform: scale(1);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    z-index: -1;
  }

  .content-illust1 {
    width: 30%vh;
    z-index: 2;
  }
</style>
