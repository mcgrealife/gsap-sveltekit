# Basic setup for gsap with ScrollTrigger

- Visible at [https://gsap-sveltekit-mcgrealife.vercel.app/](https://gsap-sveltekit-mcgrealife.vercel.app/)
- Currently relies on disabling server side rendering
- And invoking gsap methods after onMount
- note: if viewing this after 1 year, CSS @scroll-timeline is probably a better option (currently it's only available in chrome, and still experimental) [video](https://youtu.be/mzKfetD9YrA)
- I found gsap after hitting limitations while using svelte window:scrolly binding, and the svelte package in-view (it only triggered when the object entered or left the viewport). Svelte transitions were also limited to creating/destroying object triggers.  Framer motion was also similarly limited. I did hack my way around to transform objects on scroll, but it wasn't flexible. GSAP seems like a great solution for now (and much more lighweight than other solutions such as scroll-magic).
- wow gsap is excellent. I'm using scrollTrigger and TextPlugin (together). I have since linked it to lottie JSON animations (made in After Effects).
- note to self: use .lottie files instead of .json files to utilize the VScode lottie extension (which allows easy manipulation of frame rate and colors)
- this app also displays 3 different ways to add a lottie animation. (gsap works best without the lottie-player, and just the basic lottie-web import).