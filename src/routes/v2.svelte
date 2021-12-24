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
  import Spacer from "../components/Spacer.svelte";
  import { onMount } from "svelte";
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger.js";
  import { TextPlugin } from "gsap/dist/TextPlugin.js";
  import lottie from "lottie-web";

  let innerWindowWidth;
  $: desktop = innerWindowWidth >= 900;

  gsap.registerPlugin(ScrollTrigger);
  gsap.registerPlugin(TextPlugin);

  onMount(() => {
    // gsap.from(".phone-outline", {
    //   duration: 0.8,
    //   ease: "easeOut",
    //   //   height: "+=200",
    //   width: "+=1500",
    //   opacity: 0,
    // });

    gsap.to(".property", {
      ease: "none",
      y: "-=1100",
      scrollTrigger: {
        trigger: ".spacer4",
        // start: "top center",
        scrub: 0,
        markers: true,
      },
    });
  

  gsap.to(".nav", {
      ease: "none",
      y: "+=100",
      scrollTrigger: {
        trigger: ".spacer4",
        // start: "top center",
        scrub: 1,
        markers: true,
      },
    });


    // try to make small-header reverse at the slightest scroll oppositie direction
    gsap.to(".small-header", {
      ease: "none",
      opacity: "+=100",
      scrollTrigger: {
        trigger: ".spacer4",
        // toggleActions: "play play reverse reverse",
        // start: "top center",
        end: "10px",
        scrub: 2,
        markers: true,
      },
    });

  });

  function handleClick() {
    window.location.href = "/";
  }
</script>


<svelte:window bind:innerWidth={innerWindowWidth} />

<div class="scroll">
  <div class="gridContainer" style="background-color: blue">
    <div class="spacer1" />
    <!-- <img class="fitColWidth mask" src="mask-phone-only.svg" alt="mask" /> -->
    <div class="phone-container" style="background-color: red">
      <!-- <img class="phone-content fillColWidth" src="phone-screens/v2.png" alt="home"/> -->
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
    <div class="spacer2" />
  </div>
  <div class="spacer3" >spacer3</div>
  <div class="spacer4" >spacer4</div>
  <!-- <button class="btn" on:click|preventDefault="{handleClick}">Go back to main page</button> -->

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
    grid-template-columns: repeat(2, 1fr) 230px repeat(2, 1fr);
    grid-template-rows: 1fr 472px 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;
  }

  .scroll {
    height: 300vh;

  }

  .spacer1 {
    height: 100px;
    background-color: red;
    grid-area: 1/1/1/6;
  }

  .spacer2 {
    height: 100px;
    background-color: yellow;
    grid-area: 3/1/3/6;
  }

  .spacer3 {
    height: 500px;
    background-color: green;
  }

  .spacer4 {
    height: 100px;
    background-color: green;
  }

  .phone-container {
    overflow-y: hidden;
    grid-area: 2/3/3/4;
    display: grid;
    grid-template-columns: 10.5px 209px 10.5px;
    grid-template-rows: 10px 24.5px 420px 8px 10px;
    /* center row 420px */
    grid-column-gap: 0px;
    grid-row-gap: 0px;
  }

  .overlay {
    z-index: 3;
  }

  .phone-content {
    grid-area: 3/2/3/3;
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
  }

  .small-header {
    grid-area: 3/2/4/3;
    align-self: start;
    opacity: 0;
    z-index: 2;
  }

  .fillColWidth {
    max-width: 100%;
    height: auto;
  }

  .fitColWidth {
    /* object-fit: cover; */
    /* height: auto; */
    /* width: 100%; */
    grid-area: 1/1/3/5;
  }

  .mask {
    grid-area: 1/3/1/4;
    /* z-index: 2; */
  }

  .btn {
      display: grid;
      height: 100px;
      width: 50%;
      justify-content: center;

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
