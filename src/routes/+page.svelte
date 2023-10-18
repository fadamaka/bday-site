<script>
  import ConfettiHover from "../components/ConfettiHover.svelte";
  import DownArrow from "../components/DownArrow.svelte";
  import GiftBox from "../components/GiftBox.svelte";
  import { Confetti } from "svelte-confetti";

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
      delay={[100, 5000]}
      iterationCount={2}
      duration={5000}
      amount={800}
      fallDistance="100vh"
    />
  </div>
  <section>
    <ConfettiHover />
    <nav class="nav">
      <DownArrow handleClick={scrollIntoView} href="#gifts" />
    </nav>
  </section>
  <section id="gifts">
    <GiftBox />
  </section>
</main>

<style>
  :global(body) {
    background-color: #21d4fd;
    background-image: linear-gradient(19deg, #21d4fd 0%, #b721ff 100%);
    font-family: Helvetica, sans-serif;
    height: 100vh;
    margin: 0;
  }
  .nav {
    font-family: Helvetica, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 10vh;
  }
  section {
    min-height: 100vh;
  }
</style>
