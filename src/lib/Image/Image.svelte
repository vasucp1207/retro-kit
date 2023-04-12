<script>
  import { onMount } from "svelte";

  export let src = "";
  export let alt = "image not found";
  export let width = 400;
  export let height = 300;
  export let border = false;
  export let bars = false;
  export let slide = false;
  export let dimen = "";

  let borderClass = "";

  $: if (border) {
    borderClass = "border-2 border-[#bc93f9]";
  }

  onMount(() => {
    let c = document.createElement("canvas");
    let ctx = c.getContext("2d");
    let img1 = new Image();
    img1.crossOrigin = "anonymous";

    img1.onload = function () {
      let w = img1.width;
      let h = img1.height;

      c.width = w;
      c.height = h;
      ctx.drawImage(img1, 0, 0);

      ctx.fillStyle = "#ffffff";
      ctx.fillRect(0, 0, w, h);

      ctx.drawImage(img1, 0, 0);

      var pixelArr = ctx.getImageData(0, 0, w, h).data;
      let sample_size = 20;

      for (let y = 0; y < h; y += sample_size) {
        for (let x = 0; x < w; x += sample_size) {
          let p = (x + y * w) * 4;
          ctx.fillStyle =
            "rgba(" +
            pixelArr[p] +
            "," +
            pixelArr[p + 1] +
            "," +
            pixelArr[p + 2] +
            "," +
            pixelArr[p + 3] +
            ")";
          ctx.fillRect(x, y, sample_size, sample_size);
        }
      }

      let img2 = new Image();
      img2.src = c.toDataURL("image/jpeg");
      img2.width = 300;
      img2.height = 300;
      src = img2.src;
    };
    img1.src = src;
  });
</script>

{#if !bars && !slide}
  <img
    id="image1"
    {src}
    {alt}
    {width}
    {height}
    class={`${borderClass} object-cover`}
  />
{:else if slide}
  <img class="h-full w-full object-cover" id="image1" {src} alt="slide-img" />
{:else if bars}
  <img class={dimen} {src} alt="slide-img" />
{/if}

<style>
</style>
