<div class="popup" id="ytvideo">
  <div class="popup-inner">
    <div class="popup__photo">
      <iframe
        src="https://www.youtube.com/embed/AfRyM57Ky2s?si=EqgmypKBFucYFM1j"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowfullscreen
      />
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

  html,
  body {
    font-family: "Raleway", sans-serif;
    font-size: 16px;
  }

  @media screen and (max-width: 80vh) {
    html,
    body {
      font-size: 12px;
    }
  }

  .container {
    background-color: $main-color;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100vw;
    height: 80vh;
  }

  .button {
    text-decoration: none;
    font-size: 0.875rem;
    font-weight: 300;
    text-transform: uppercase;
    display: inline-block;
    border-radius: 1.5rem;
    background-color: #fff;
    color: $main-color;
    padding: 1rem 2rem;
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
      position: relative;
      bottom: -100vw;
      right: -100vh;
      display: flex;
      transform: rotate(32deg);
      transition: 0.64s ease-in-out;
      align-items: center;
    }
    &__photo {
      display: block;
      justify-content: flex;
      align-items: flex;
      overflow: hidden;
      iframe {
        width: 142vh;
        height: 81vh;
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
