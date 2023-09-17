<script>
    import { onMount } from "svelte";
    import gsap from "gsap";
    import {ScrollTrigger} from "gsap/dist/ScrollTrigger";
  
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
      gsap.registerPlugin(ScrollTrigger);
  
    console.clear();
    
    const factor = 2
    
    gsap.set('.center', {xPercent:-50, yPercent:-50})
    gsap.set('section', { autoAlpha: 0 })
    
    
    
    var sections = gsap.utils.toArray("section:not(.end)");
    
    var largeTL = gsap.timeline({
        scrollTrigger: { 
        trigger: '.wrap-all',
        pin: true,
        scrub: 0.5,
        start: "top top",
        end: "+=" + (sections.length * 100 * factor) + "%",
        //   markers: true
        },
    })
    
    sections.forEach(function(elem,i) {
    
        gsap.set("section", {zIndex: (i, target, targets) => targets.length - i});    
    
        // select the relevant elements  
        var lines = elem.querySelectorAll(".lines");
    
        var first = elem.querySelectorAll(".lines.first");
        var second = elem.querySelectorAll(".lines.second");
    
        const tldelay = i * factor;  
        const tweenduration = 1/13 * factor  // -->  1/cumulated duration of all tweens here * factor
    
        var smallTL = gsap.timeline()
    
        smallTL
        
        .to(elem, { autoAlpha: 1, duration: tweenduration })
        
        .from(first, {xPercent: -100, duration: tweenduration*2, ease:'power2.inOut'}) 
        
        .to({}, {duration: tweenduration }) // a little pause in between
        
        .to(first, {xPercent: 100, duration: tweenduration*2, ease:'power2.inOut'}) 
        
        .to({}, {duration: tweenduration/2 }) // a little pause in between
        
        .from(second, {xPercent: -100, duration: tweenduration*2, ease:'power2.inOut'}) 
        
        .to({}, {duration: tweenduration/2 }) // a little pause in between
        
        .to(second, {xPercent: 100, duration: tweenduration*2, ease:'power2.inOut'}) 
        
        .to(elem, { autoAlpha: 0, duration: tweenduration })
    
        .to({}, {duration: tweenduration}) // a little pause at the end
    
        ;
    
        largeTL.add(smallTL, tldelay);
        //largeTL.add(smallTL, tldelay - (tldelay*tweenduration));
  
  })
  
  
  
  var endTL = gsap.timeline({
    scrollTrigger: { 
      trigger: '.trigger',
      pin: '.wrap-all',
      scrub: 0.5,
      start: "top top-=" + (sections.length * 100 * factor) + "%",
      end: "+=" + 10 * factor + "%"
    },
  })
  
  endTL
  
  .to('section.end', { autoAlpha: 1, duration: 1 * factor })
  
  //.to('section.end', { autoAlpha: 1, duration: 0.5 * factor })
  //.to({}, { duration: 1 * factor })
    })
  </script>
  
  <div>
  <div class="trigger">
    <div class="wrap-all">
    
    <section class="section section01"> 
      <h1>Section 01</h1>
    
      <div class="wrap center">
        <h2 class="lines first">First BREAK!</h2>
      </div>
      
      <div class="wrap center">
        <h2 class="lines second">First COFFEE!</h2>
      </div>
    
    </section>
    
    <section class="section"> 
      <h1 class="line">Section 02</h1> 
    
      <div class="wrap center">
        <h2 class="lines first">Second BREAK!</h2>
      </div>
      
      <div class="wrap center">
        <h2 class="lines second">Second COFFEE!</h2>
      </div>
    
    </section>
    
    <section class="section"> 
      <h1 class="line">Section 03</h1>
    
      <div class="wrap center">
        <h2 class="lines first">Third BREAK!</h2>
      </div>
      
      <div class="wrap center">
        <h2 class="lines second">Third COFFEE!</h2>
      </div>
    
    </section>
    
    <section class="section end"> 
      <h1>End</h1>  
    </section>
      
    </div>
    </div>
  </div>
  
  
  
  <style>
  
  body{
    background-color:white;
    margin:0;
  }
  
  section{
    position: absolute;
    top:0;
    left:0;
    width:100%;
    height:100vh;
    border-bottom:1px solid black;
    background-color: white;
  }
  
  h1{
    position: absolute;
    font-size: 19vw;
    font-family: sans-serif;
    line-height: 40vh;
    color: #a7a7a733;
    margin: 0 0 0 20px;
  }
  
  .wrap{
    position: absolute;
    top: 50%;
    left: 50%;
    width: fit-content;
    overflow:hidden;
  }
  .wrap h2{
    position:relative;
    font-family: sans-serif;
    font-size: 4vw;
    margin:0;
  }
  .wrap-all {
    min-height: 100vh;
  }
  </style>