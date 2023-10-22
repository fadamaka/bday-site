<script>
  export let elementId = "";
  export let imgSrc = "";
  export let webpSrc = "";
  export let giftSrc = "";
  export let played = false;

  function changeSrc() {
    if (!played) {
      imgSrc = webpSrc;
      setTimeout(() => {
        imgSrc = giftSrc;
      }, 4700);
      played = true;
    }
  }
</script>

<img id={elementId} src={imgSrc} alt="" on:click={() => changeSrc()} />

<style>
  img {
    justify-content: center;
    align-items: center;
    height: auto;
    width: auto;
    max-width: 512px;
  }
</style>
