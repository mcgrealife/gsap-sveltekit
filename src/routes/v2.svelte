<script context="module">
  export const ssr = false;
</script>

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

  let color = {
    primaryBlue: "#366CA5",
    primaryDark: "#3C4043",
  };

  onMount(() => {
    // gsap.from(".phone-outline", {
    //   duration: 0.8,
    //   ease: "easeOut",
    //   //   height: "+=200",
    //   width: "+=1500",
    //   opacity: 0,
    // });

    // gsap lottie helper function
    // https://greensock.com/docs/v3/HelperFunctions#lottie
    function LottieScrollTrigger(vars) {
      let playhead = { frame: 0 },
        target = gsap.utils.toArray(vars.target)[0],
        speeds = { slow: "+=2000", medium: "+=1000", fast: "+=500" },
        st = {
          trigger: target,
          pin: true,
          start: "top top",
          end: speeds[vars.speed] || "+=1000",
          scrub: 1,
        },
        animation = lottie.loadAnimation({
          container: target,
          renderer: vars.renderer || "svg",
          loop: false,
          autoplay: false,
          path: vars.path,
        });
      for (let p in vars) {
        // let users override the ScrollTrigger defaults
        st[p] = vars[p];
      }
      animation.addEventListener("DOMLoaded", function () {
        gsap.to(playhead, {
          frame: animation.totalFrames - 1,
          ease: "none",
          onUpdate: () => animation.goToAndStop(playhead.frame, true),
          scrollTrigger: st,
        });
        // in case there are any other ScrollTriggers on the page and the loading of this Lottie asset caused layout changes
        ScrollTrigger.sort();
        ScrollTrigger.refresh();
      });
      return animation;
    }

    LottieScrollTrigger({
      target: "#mainLottie",
      path: "source.json",
      speed: "medium",
      scrub: 1, // seconds it takes for the playhead to "catch up"
      // you can also add ANY ScrollTrigger values here too, like trigger, start, end, onEnter, onLeave, onUpdate, etc. See https://greensock.com/docs/v3/Plugins/ScrollTrigger
    });

    gsap.to("#textplugin", {
      duration: 3,
      // delay: 1,
      text: "Resider solely consists of rental properties syndicated through data API’s. With up to date and accurate listings, your clients can browse with confidence.",
      ease: "none", //Power1.easeOut

      scrollTrigger: {
        trigger: "#textplugin",
        start: "top center",

        // markers: true,
        toggleActions: "play play play play",
      },
    });
  });
</script>

<svelte:head>
  <script
    src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/gsap.min.js"></script>
  <script
    src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/ScrollTrigger.min.js"></script>
</svelte:head>

<svelte:window bind:innerWidth={innerWindowWidth} />

<div class="gridContainer" style="background-color: blue">
  <!-- <div class="mask">
    <img class="fitColWidth" src="mask-phone-only.svg" alt="mask" />
  </div> -->
  <div class="phone-container" style="background-color: red">
    <img class="fitColWidth" src="iPhone-Frame.svg" alt="iPhone-frame" />
    <div class="home">
      <img class="fillColWidth" src="phone-screens/v2.png" alt="home" />
    </div>
  </div>
</div>

<style>
  * {
    font-family: "Gilroy", "Open Sans", -apple-system;
    overflow-x: hidden;
  }

  .gridContainer {
    display: grid;
    grid-template-columns: repeat(2, 1fr) 230px repeat(2, 1fr);
    grid-template-rows: 1fr 472px 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;

    /* justify-items: center; */
  }

  .phone-container {
    grid-area: 2/3/3/4;
    display: grid;
    grid-template-columns: 10.5px 209px 10.5px;
    grid-template-rows: 10px 24.5px 1fr 8px 10px;
    grid-column-gap: 0px;
    grid-row-gap: 0px;
  }

  .phone-outline {
    grid-area: 1/1/3/5;
  }
  .home {
    grid-area: 2/2/5/3;
  }

  .fillColWidth {
    max-width: 100%;
    height: auto;
  }
  /* https://stackoverflow.com/questions/46090760/controlling-the-size-of-an-image-within-a-css-grid-layout */
  
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
