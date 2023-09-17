<script>
  // import components
  import Backgroud from "./../../components/intro/Backgroud.svelte";
  import FloatNav from "./../../components/nav/FloatNav.svelte";

  // import svelte
  import { onMount } from "svelte";
  import Saos from "saos";
  import { bounceOut } from "svelte/easing";
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
        start: "top 60%",
        end: "center 40%",
        toggleActions: "restart none none reverse",
      },
    });

    const tl_1 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec1",
        start: "center 60%",
        end: "center 40%",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_2 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec2",
        start: "top 60%",
        end: "center 40%",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_3 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec3",
        start: "top 60%",
        end: "center 40%",
        toggleActions: "restart reverse complete reverse",
      },
    });

    const tl_4 = gsap.timeline({
      scrollTrigger: {
        markers: "true",
        trigger: ".animate-sec4",
        start: "top 60%",
        end: "center 40%",
        toggleActions: "restart reverse complete reverse",
      },
    });

    tl_0.fromTo(
      ".content-bg1",
      { opacity: 0, duration: 0.5, y: "-20%" },
      {
        ease: bounceOut,
        duration: 0.5,
        y: "0",
        position: "fixed",
        opacity: 1,
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
        { ease: bounceOut, duration: 0.5, y: "100%", opacity: 1 }
      )
      .fromTo(
        ".sec2-elem2",
        { opacity: 0, duration: 0.5, y: "-20%" },
        { ease: bounceOut, duration: 0.5, y: "100%", opacity: 1 }
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
    <div class="row m-4">
      <div class="col-md-12">
        <!--  -->
      </div>
    </div>
  </section>
  <!-- definisi -->

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
    transform: scale(0.8);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    z-index: -1;
  }

  .content-illust1 {
    width: 500px;
    z-index: 2;
  }
</style>
