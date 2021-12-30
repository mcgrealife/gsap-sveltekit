<script context="module">
  export const ssr = false;
</script>

<svelte:head>
  <script
    src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/gsap.min.js"></script>
  <script
    src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/ScrollTrigger.min.js"></script>
</svelte:head>


<script>
  import { onMount } from "svelte";
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger.js";

  gsap.registerPlugin(ScrollTrigger);
  

  onMount(() => {

    gsap.to(".property", {
      ease: "none",
      y: "-=1800",
      scrollTrigger: {
        // trigger: ".spacer4",
        // start: "top center",
        scrub: 0,
        // markers: true,
      },
    });
  

  gsap.to(".nav", {
      ease: "none",
      y: "+=100",
      scrollTrigger: {
        // trigger: ".spacer4",
        // start: "top center",
        scrub: 1,
        // markers: true,
      },
    });


    // try to make small-header reverse at the slightest scroll oppositie direction
    gsap.to(".small-header", {
      ease: "none",
      opacity: "+=100",
      scrollTrigger: {
        trigger: ".property",
        // toggleActions: "play play reverse reverse",
        start: "middle -300px",
        // end: "10px",
        scrub: 2,
        markers: true,
      },
    });





  });

</script>



<div class="scroll">
  <div class="gridContainer">

    <div class="phone-container">
      <img
        class="phone-content fillColWidth property"
        id="property"
        src="phone-screens/property-tall.png"
        alt="property-tall"
      />
      <img class="swiper fillColWidth overlay" src="swiper.png" alt="swiper" />

      <img class="nav fillColWidth overlay" src="phone-screens/property-nav-no-shadow.png" alt="nav-bar">

      <img class="small-header fillColWidth overlay" src="small-header.png" alt="small-header">

      <img
        class="status-bar fillColWidth overlay"
        src="status-bar.png"
        alt="status-bar"
      />

      <img
        class="fitColWidth overlay"
        src="iPhone-Frame.svg"
        alt="iPhone-frame"
      />
      
      

    </div>
    
  </div>
 

</div>


<style>
  * {
    font-family: "Gilroy", "Open Sans", -apple-system;
  }

  .gridContainer {
    position: -webkit-sticky;
    position: sticky;
    top: 0px;
    display: grid;
    grid-template-columns: repeat(2, 1fr) 398px repeat(2, 1fr);
    grid-template-rows: 1fr 818.5px 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;
    height: 100vh;
    
  }

  .phone-container {
    overflow-y: hidden;
    grid-area: 2/3/3/4;
    display: grid;
    grid-template-columns: 1fr 362px 1fr;
    grid-template-rows: 18px 43px 740px 8px 10px;
    /* center row 420px */
    grid-column-gap: 0px;
    grid-row-gap: 0px;
    overscroll-behavior-y: none;  
  }

  .scroll {
    height: 300vh;
    overscroll-behavior-y: none;  
  }



  .overlay {
    z-index: 3;
  }

  .phone-content {
    grid-area: 3/2/3/3;
    will-change: transform;
  }

  .status-bar {
    grid-area: 2/2/3/3;
  }

  .swiper {
    grid-area: 4/2/5/3;
  }

  .nav {
    grid-area: 3/2/5/3;
    align-self: end;
    z-index: 2;
    will-change: transform;
  }

  .small-header {
    grid-area: 3/2/4/3;
    align-self: start;
    opacity: 0;
    z-index: 2;
    will-change: transform;
  }

  .fillColWidth {
    max-width: 100%;
    height: auto;
  }

  .fitColWidth {
    object-fit: cover;
    height: auto;
    width: 100%;
    grid-area: 1/1/3/5;
  }


  @font-face {
    font-family: "Gilroy";
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: local("Gilroy"), local("Gilroy-Regular"),
      url("./regular.woff2") format("woff2"),
      url("./regular.woff") format("woff");
  }

  @font-face {
    font-family: "Gilroy";
    font-style: normal;
    font-weight: 500;
    font-display: swap;
    src: local("Gilroy Medium"), local("Gilroy-Medium"),
      url("./medium.woff2") format("woff2"), url("./medium.woff") format("woff");
  }

  @font-face {
    font-family: "Gilroy";
    font-style: normal;
    font-weight: 600;
    font-display: swap;
    src: local("Gilroy SemiBold"), local("Gilroy-SemiBold"),
      url("./semi-bold.woff2") format("woff2"),
      url("./semi-bold.woff") format("woff");
  }

  @font-face {
    font-family: "Gilroy";
    font-style: italic;
    font-weight: 400;
    font-display: swap;
    src: local("Gilroy Italic"), local("Gilroy-Italic"),
      url("./italic-regular.woff2") format("woff2"),
      url("./italic-regular.woff") format("woff");
  }

  @font-face {
    font-family: "Gilroy";
    font-style: italic;
    font-weight: 500;
    font-display: swap;
    src: local("Gilroy Medium Italic"), local("Gilroy-MediumItalic"),
      url("./italic-medium.woff2") format("woff2"),
      url("./italic-medium.woff") format("woff");
  }
</style>
