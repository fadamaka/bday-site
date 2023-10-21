<script>
  import ConfettiHover from "../components/ConfettiHover.svelte";
  import DownArrow from "../components/DownArrow.svelte";
  import GiftBox from "../components/GiftBox.svelte";
  import { Confetti } from "svelte-confetti";
  import { onMount } from "svelte";
  import Carousel from "svelte-carousel";
  import { browser } from "$app/environment";

  onMount(disableScroll);
  onMount(enableScroll);
  /**
   * @param {string} target
   */
  function scrollIntoView(target) {
    const el = document.querySelector(target);
    if (!el) return;
    el.scrollIntoView({
      behavior: "smooth",
    });
  }

  // left: 37, up: 38, right: 39, down: 40,
  // spacebar: 32, pageup: 33, pagedown: 34, end: 35, home: 36
  var keys = { 37: 1, 38: 1, 39: 1, 40: 1, 32: 1, 33: 1, 34: 1, 35: 1, 36: 1 };

  // @ts-ignore
  function preventDefault(e) {
    e.preventDefault();
  }

  // @ts-ignore
  function preventDefaultForScrollKeys(e) {
    // @ts-ignore
    if (keys[e.keyCode]) {
      preventDefault(e);
      return false;
    }
  }

  // modern Chrome requires { passive: false } when adding event
  var supportsPassive = false;
  try {
    // @ts-ignore
    window.addEventListener(
      "test",
      null,
      Object.defineProperty({}, "passive", {
        get: function () {
          supportsPassive = true;
        },
      })
    );
  } catch (e) {}

  var wheelOpt = supportsPassive ? { passive: false } : false;

  // call this to Disable
  // @ts-ignore
  function disableScroll() {
    window.addEventListener("DOMMouseScroll", preventDefault, false); // older FF
    window.addEventListener(
      "onwheel" in document.createElement("div") ? "wheel" : "mousewheel",
      preventDefault,
      wheelOpt
    ); // modern desktop
    window.addEventListener("touchmove", preventDefault, wheelOpt); // mobile
    window.addEventListener("keydown", preventDefaultForScrollKeys, false);
  }

  // call this to Enable
  // @ts-ignore
  function enableScroll() {
    setTimeout(() => {
      window.removeEventListener("DOMMouseScroll", preventDefault, false);
      // @ts-ignore
      window.removeEventListener(
        "onwheel" in document.createElement("div") ? "wheel" : "mousewheel",
        preventDefault,
        wheelOpt
      );
      // @ts-ignore
      window.removeEventListener("touchmove", preventDefault, wheelOpt);
      window.removeEventListener("keydown", preventDefaultForScrollKeys, false);
      if (document.getElementById("nav")) {
        // @ts-ignore
        document.getElementById("nav").style.setProperty("--vis", "visible");
      }
    }, 11000);
  }
</script>

<main>
  <div
    style="
 position: fixed;
 top: -50px;
 left: 0;
 height: 100vh;
 width: 100vw;
 display: flex;
 justify-content: center;
 overflow: hidden;
 pointer-events: none;"
  >
    <Confetti
      x={[-5, 5]}
      y={[0, 0.1]}
      delay={[100, 3800]}
      iterationCount={2}
      duration={3800}
      amount={800}
      fallDistance="100vh"
    />
  </div>
  <section>
    <ConfettiHover />
    <nav class="nav" id="nav">
      <DownArrow handleClick={scrollIntoView} href="#gifts" />
    </nav>
  </section>
  <section id="gifts" class="gifts">
    {#if browser}
      <Carousel>
        <GiftBox />
        <GiftBox />
        <GiftBox />
      </Carousel>
    {/if}
  </section>
</main>

<style>
  :global(body) {
    background-color: #21d4fd;
    background-image: linear-gradient(19deg, #1b4e5a 0%, #6d1f91 100%);
    font-family: Helvetica, sans-serif;
    height: 100vh;
    margin: 0;
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
  :global(body)::-webkit-scrollbar {
    display: none; /* Safari and Chrome */
  }
  .nav {
    font-family: Helvetica, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 10vh;
    visibility: var(--vis);
  }
  section {
    min-height: 100vh;
  }
  .gifts {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  :root {
    --vis: hidden;
  }
</style>
