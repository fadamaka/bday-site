<script>
  export let imgSrc = "";
  export let webpSrc = "";

  function changeSrc() {
    imgSrc = webpSrc;
  }
</script>

<img src={imgSrc} alt="" on:click={() => changeSrc()} />

<style>
  img {
    justify-content: center;
    align-items: center;
    height: auto;
    width: auto;
    max-width: 50%;
  }
</style>
