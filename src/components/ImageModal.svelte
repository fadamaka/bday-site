<script>
  export let imgSrc = "";
</script>

<div class="popup" id="wordcloud">
  <div class="popup-inner">
    <div class="popup__photo">
      <img src={imgSrc} alt="" />
      * Based on Discord activity (#general, #tl-talk) from May 2023 to October 2023
    </div>
    <a class="popup__close" href="#gifts">X</a>
  </div>
</div>

<style lang="scss">
  @import url("https://fonts.googleapis.com/css?family=Raleway:300,400,600&subset=latin-ext");

  $main-color: #9191e9;

  * {
    box-sizing: border-box;
  }

  @media screen and (max-width: 80vh) {
  }

  .popup {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    width: 100vw;
    height: 100vh;
    bottom: 0;
    right: 0;
    background-color: rgba(37, 29, 63, 0.897);
    visibility: hidden;
    opacity: 0;
    overflow: hiden;
    transition: 0.64s ease-in-out;
    &-inner {
      background-color: rgb(63, 50, 107);
      position: relative;
      bottom: -100vw;
      right: -100vh;
      display: flex;
      width: 80%;
      height: 80%;
      transform: rotate(32deg);
      transition: 0.64s ease-in-out;
      align-items: center;
    }
    &__photo {
      display: block;
      justify-content: flex;
      align-items: flex;
      overflow: hidden;
      font-size: 0.7em;

      color: #20162b;
      img {
        width: 100%;
        height: auto;
      }
    }
    &:target {
      visibility: visible;
      opacity: 1;
      .popup-inner {
        bottom: 0;
        right: 0;
        transform: rotate(0);
      }
    }
    &__close {
      position: absolute;
      right: -1rem;
      top: -1rem;
      width: 3rem;
      height: 3rem;
      font-size: 0.875rem;
      font-weight: 300;
      border-radius: 100%;
      background-color: #0a0a0a;
      z-index: 4;
      color: #fff;
      line-height: 3rem;
      text-align: center;
      cursor: pointer;
      text-decoration: none;
    }
  }
</style>
