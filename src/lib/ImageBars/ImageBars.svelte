<script>
  import Image from "$lib/Image/Image.svelte";
  import { onMount } from "svelte";

  export let imageBars = [];
  let active = 0;
</script>

<div class="flex bars gap-5 m-5">
  {#each imageBars as image, index}
    <div class="relative">
      <div>
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div on:click={() => (active = index)}>
          <Image
            bars
            src={image.src}
            alt={image.alt}
            dimen={`${
              active === index
                ? "w-[550px] h-[350px] cursor-default"
                : "w-[50px] h-[350px]"
            } border-2 object-cover cursor-pointer transition-all ease-in-out`}
          />
        </div>
      </div>
      {#if active === index}
        <a
          href={image.link}
          class="absolute top-4 left-4 text-3xl text-white flex items-center gap-2 cursor-pointer"
        >
          <svg
            height="32px"
            transform="scale(1,1)"
            version="1.1"
            viewBox="0 0 38 38"
            width="32px"
            xmlns="http://www.w3.org/2000/svg"
            ><g fill="none" fill-rule="evenodd" stroke="none" stroke-width="1"
              ><title
                >Careers site call to action icon - circle with right arrow</title
              ><g transform="translate(-5.000000, -5.000000)"
                ><g transform="translate(6.000000, 6.000000)"
                  ><circle
                    cx="18"
                    cy="18"
                    r="18"
                    stroke="#FFFFFF"
                    stroke-width="1"
                  /><g
                    stroke="#FFFFFF"
                    stroke-width="2"
                    transform="translate(11.000000, 13.000000)"
                    ><polyline
                      points="8 0 13 5 8 10"
                      stroke-linecap="square"
                    /><path d="M0,5 L13,5" /></g
                  ></g
                ></g
              ></g
            ></svg
          >
          <div>Read More</div>
        </a>

        <div class="absolute bottom-2 left-4 flex flex-col text-white">
          <div class="text-3xl">{image.title}</div>
          <div class="text-2xl">{image.description}</div>
        </div>
      {/if}
    </div>
  {/each}
</div>

<style>
  .bars {
    font-family: "VT323";
  }
</style>
