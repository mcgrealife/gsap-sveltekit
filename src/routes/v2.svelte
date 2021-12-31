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
  import { Flip } from "gsap/dist/Flip.js";
  import { TextPlugin} from "gsap/dist/TextPlugin.js";

  gsap.registerPlugin(ScrollTrigger);
  gsap.registerPlugin(Flip);
  gsap.registerPlugin(TextPlugin);

  onMount(() => {

    // const runOnComplete = () => {
    //   gsap.to(".availability", {
    //   ease: "none",
    //   opacity: 100,
          
    // });
    // }

   
    // gsap.to(".scroll", {
    //   ease: "none",
    //   // onComplete: runOnComplete,
    //   scrollTrigger: {
    //     // trigger: ".scroll",
    //     // start: "middle top", 
    //     pin: ".gridContainer",
    //     scrub: 1,
    //     // markers: true,
    //   },
    // });


    const tl = gsap.timeline();

    tl.to(".property", {y: -1875})
      .to(".small-header", {opacity: "+=100", duration: 0.1}, "<6.7%")
      .to(".text", {left: "+=800"}, "<25%")
      .set(".text", {text: "Public posting prohibited"}, "<30%")
      .to(".availability", {left: 0});
    
      ScrollTrigger.create({
        animation: tl,
        trigger: "#gridContainer",
        start: "top top",
        end: "+=5000",
        scrub: 2,
        pin: true,
        anticipatePin: 1,
      })

  });

</script>


  <div class="scroll">

    <div class="section1" data-speed=".4">
      <h1 class="welcomeText">A better way to generate leads</h1>   
      
    </div>

    <div id="gridContainer"  class="gridContainer">
  
      <div id= "text" class="text">Syndicated data only</div>
  
  
      <div class="phone-container">
        
        <img
          class="fillColWidth property"
          id="property"
          src="phone-screens/property-tall.png"
          alt="property-tall"
        />
        <img class="swiper fillColWidth overlay10" src="swiper.svg" alt="swiper" />
  
        <img class="fillColWidth availability overlay4" src="availability.png" alt="availability" >
  
  
        <img class="nav fillColWidth overlay5" src="nav.png" alt="nav">
  
        <img class="small-header fillColWidth overlay" src="small-header.png" alt="small-header">
  
        <img
          class="status-bar fillColWidth overlay"
          src="status-bar.png"
          alt="status-bar"
        />
  
        <img
          class="fitColWidth overlay10"
          src="iPhone-Frame.svg"
          alt="iPhone-frame"
        />
      </div>
    </div>
    <div class="section2">
      <div class="direct-data">
        <h1>Direct Data only. No public postings allowed.</h1>
      </div>
    </div>
    <div class="section3" />
    <div class="section4" />
    <div class="section5" />
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
    place-content: center;
    grid-template-columns: 400px 398px 400px;
    grid-template-rows: 1fr 818.5px 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;
    height: 100vh;
    
  }

  .phone-container {
      overflow-y: hidden;
      grid-area: 2/2/3/3;
      display: grid;
      grid-template-columns: 1fr 362px 1fr;
      grid-template-rows: 18px 43px 740px 18px;
      /* center row 420px */
      grid-column-gap: 0px;
      grid-row-gap: 0px;
      overscroll-behavior-y: none;  
  }

  .scroll {
    /* height: 500vh; */
    overscroll-behavior-y: none; 
    background-color: white; 
  }

  .welcomeText {
    color: white;
    font-weight: 400;
    font-size: 50px;
  }

  .section1 {
    display: grid;
    place-content: center;
    height: 50vh;
    background-color: #366CA5;
    
  }
  .section2 {
    height: 100vh;
    background-color:#366CA5;
  }

  .section3 {
    height: 100vh;
    background-color:red;
  }

  .section4 {
    height: 100vh;
    background-color:green;
  }
  .section5 {
    height: 100vh;
    background-color:pink;
  }
.text {
  opacity: 1000;
  grid-area: 2/1/3/2;
  align-self: center;
  justify-self: center;
  text-align: center;
  position: relative;
  font-size: 72px;
  color: black;
  mix-blend-mode: lighten;
 
}


  
  .availability {
    grid-area: 3/2/4/3;
    position: relative;
    height: auto;
    right: -362px;    
  }

  .direct-data {
    opacity:0;
  }


  .overlay {
    z-index: 3;
  }

  .property {
    grid-area: 3/2/3/3;
    will-change: transform;
  }

  .status-bar {
    grid-area: 2/2/3/3;
  }

  .swiper {
    grid-area: 3/2/4/3;
      align-self: end;
      object-fit: cover;
      height: auto;
      width: 100%;
  }

  .nav {
    grid-area: 3/2/4/3;
    align-self: end;
    z-index: 2;
    will-change: transform;
    box-shadow: 0px -2.00133px 4.00267px rgba(60, 64, 67, 0.1);
  }

  .small-header {
    grid-area: 3/2/4/3;
    align-self: start;
    opacity: 0;
    z-index: 2;
    will-change: transform;
    box-shadow: 0px 4px 4px -2px rgba(60, 64, 67, 0.12);
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


  .overlay1 {
        z-index: 1;
    }

    .overlay2 {
        z-index: 2;
    }
  
    .overlay3 {
      z-index: 3;
    }

  
    .overlay3 {
        z-index: 3;
    }

    .overlay4 {
        z-index: 4;
    }

    .overlay5 {
        z-index: 5;
    }

   

    .overlay10 {
        z-index: 10;
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
