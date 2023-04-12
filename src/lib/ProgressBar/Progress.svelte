<script>
  import { onMount } from 'svelte';

  export let value = 0;
  export let bg = "#9547b7";

  let voilet = "#9547b7";
  let lightVoilet = "#bc93f9";
  let red = "#ff0000";
  let orange = "#fc4501";
  let green = "#92cc42";
  let blue = "#40b3ff";
  let black = "#212529";

  if (bg === "orange") bg = orange;
  else if (bg === "green") bg = green;
  else if (bg === "voilet") bg = voilet;
  else if (bg === "blue") bg = blue;
  else if (bg === "dark") bg = black;
  else if (bg === "red") bg = red;

  onMount(() => {
    document.documentElement.style.setProperty("--bg", bg);
  });
</script>

<div class="progress m-5 relative flex w-fit border-2 p-[1px] border-black">
  <progress class="progress-bar relative h-7 w-80" max="100" {value} />
  <div class="absolute left-[5px] bottom-0">{value}%</div>

  <span class="absolute w-1 h-1 bg-white -top-[3px] -left-[3px]" />
  <span class="absolute w-1 h-1 bg-white -top-[3px] -right-[3px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[3px] -left-[3px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[3px] -right-[3px]" />
</div>

<style>
  :global(.progress-bar::-webkit-progress-value) {
    background: var(--bg);
    height: 100%;
    transition: width 0.3s ease-in-out;
    opacity: 0.5;
  }
  .progress {
    font-family: "VT323", monospace;
    font-size: 20px;
  }
  .progress-bar::-webkit-progress-bar {
    background: #d3d3d3;
  }
</style>
