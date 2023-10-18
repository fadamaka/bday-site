<script>
  export let handleClick = (/** @type {string} */ x) => {};
  export let href = "";
</script>

<div
  class="container"
  on:click={() => handleClick(href)}
  on:keydown={() => handleClick(href)}
  tabindex="0"
  role="button"
  aria-pressed="false"
>
  <div class="content">
    <h1>Gifts</h1>
    <svg id="more-arrows">
      <polygon
        class="arrow-top"
        points="37.6,27.9 1.8,1.3 3.3,0 37.6,25.3 71.9,0 73.7,1.3 "
      />
      <polygon
        class="arrow-middle"
        points="37.6,45.8 0.8,18.7 4.4,16.4 37.6,41.2 71.2,16.4 74.5,18.7 "
      />
      <polygon
        class="arrow-bottom"
        points="37.6,64 0,36.1 5.1,32.8 37.6,56.8 70.4,32.8 75.5,36.1 "
      />
    </svg>
  </div>
</div>

<style lang="scss">
  /* Markup */

  .container {
    padding: 20px;
    text-align: center;
  }

  .content {
    transform: translate(-50%, -50%);

    h1 {
      margin: 0 0 20px;
      color: #fff;
      font-size: 1.5em;
    }
  }

  /* Arrow & Hover Animation */
  #more-arrows {
    width: 75px;
    height: 65px;

    &:hover {
      polygon {
        fill: #fff;
        transition: all 0.2s ease-out;

        &.arrow-bottom {
          transform: translateY(-18px);
        }

        &.arrow-top {
          transform: translateY(18px);
        }
      }
    }
  }

  polygon {
    fill: #fff;
    transition: all 0.2s ease-out;

    &.arrow-middle {
      opacity: 0.75;
    }

    &.arrow-top {
      opacity: 0.5;
    }
  }
</style>
