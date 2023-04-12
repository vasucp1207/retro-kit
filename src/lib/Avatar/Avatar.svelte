<script>
  import { onMount } from "svelte";

  export let src = "";
  export let initial = "";
  export let broken = false;
  export let size = "lg";
  export let pixelize = 10;

  let height, width;
  if (size == "lg") (height = "h-14"), (width = "w-14");
  else if (size === "xl") (height = "h-16"), (width = "w-16");
  else if (size === "sm") (height = "h-12"), (width = "w-12");
  else (height = "h-10"), (width = "w-10");

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

      ctx.fillStyle = "white";
      ctx.fillRect(0, 0, w, h);

      ctx.drawImage(img1, 0, 0);

      var pixelArr = ctx.getImageData(0, 0, w, h).data;
      let sample_size = pixelize;

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

<div
  class={`avatar m-5 ${height} ${width} overflow-hidden bg-[#e4e6ea] rounded-[50%] flex justify-center items-center`}
>
  {#if src}
    <img class={`${height} ${width} object-cover`} {src} alt="avatar-img" />
  {:else if broken}
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="80%"
      height="auto"
      viewBox="0 0 24 24"
      fill="currentColor"
      ><path
        fill="currentColor"
        d="M12,4A4,4 0 0,1 16,8A4,4 0 0,1 12,12A4,4 0 0,1 8,8A4,4 0 0,1 12,4M12,14C16.42,14 20,15.79 20,18V20H4V18C4,15.79 7.58,14 12,14Z"
      /></svg
    >
  {:else}
    <div class="text-4xl">{initial}</div>
  {/if}
</div>

<style>
  .avatar {
    font-family: "VT323";
  }
</style>
