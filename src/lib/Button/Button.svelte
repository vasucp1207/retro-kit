<script>
  import { createEventDispatcher } from "svelte";

  export let bg = "bg-[#9547b7]";
  export let text = "text-white";
  export let outlined = false;
  export let href = "";

  let mouseover = false;

  let voilet = "bg-[#9547b7]";
  let red = "bg-[#ff0000]"
  let orange = "bg-[#fc4501]";
  let green = "bg-[#92cc42]";
  let blue = "bg-[#40b3ff]";
  let black = "bg-[#212529]";

  if(bg === "orange") bg = orange;
  else if(bg === "green") bg = green;
  else if(bg === "voilet") bg = voilet;
  else if(bg === "blue") bg = blue;
  else if(bg === "dark") bg = black;
  else if(bg === "red") bg = red;

  let shadow = "";
  for(let i = 4; i < bg.length - 1; i++) {
    shadow += bg[i];
  }

  const dispatch = createEventDispatcher();
  function onClick() {
    dispatch("click");
  }
</script>

{#if !outlined && href === ""}
  <button
    on:click={onClick}
    class={`relative m-5 p-[6px] ${bg} ${text} text-2xl border-2 hover:opacity-75`}
    ><slot /></button
  >
{:else if !outlined && href !== ""}
  <a {href}>
    <button
      class={`relative p-[6px] m-5 ${bg} ${text} text-2xl border-2 hover:opacity-75`}
      ><slot /></button
    >
  </a>
{:else}
  <button
    on:mousemove={() => mouseover = true}
    on:mouseleave={() => mouseover = false}
    on:click={onClick}
    class={`outlined relative p-[6px] m-5 bg-white text-2xl hover:opacity-75`}
  >
    <slot />
  </button>
{/if}

<style lang="postcss">
  @import url(https://fonts.googleapis.com/css?family=VT323);

  button {
    font-weight: bold;
    border: 3px solid black;
    font-family: "VT323", monospace;
    border-image-slice: 3;
    border-image-width: 3;
    border-image-repeat: stretch;
    border-image-source: url('data:image/svg+xml;utf8,<?xml version="1.0" encoding="UTF-8" ?><svg version="1.1" width="8" height="8" xmlns="http://www.w3.org/2000/svg"><path d="M3 1 h1 v1 h-1 z M4 1 h1 v1 h-1 z M2 2 h1 v1 h-1 z M5 2 h1 v1 h-1 z M1 3 h1 v1 h-1 z M6 3 h1 v1 h-1 z M1 4 h1 v1 h-1 z M6 4 h1 v1 h-1 z M2 5 h1 v1 h-1 z M5 5 h1 v1 h-1 z M3 6 h1 v1 h-1 z M4 6 h1 v1 h-1 z" fill="rgb(33,37,41)" /></svg>');
    border-image-outset: 2;
  }
</style>
