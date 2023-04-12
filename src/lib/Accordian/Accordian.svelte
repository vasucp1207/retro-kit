<script>

  export let title = "no title";
  export let content = "no content provided";
  export let highlight = "bg-[#9547b7]";
  
  let voilet = "bg-[#9547b7]";
  let lightVoilet = "bg-[#bc93f9]";
  let red = "bg-[#ff0000]";
  let orange = "bg-[#fc4501]";
  let green = "bg-[#92cc42]";
  let blue = "bg-[#40b3ff]";
  let black = "bg-[#212529]";

  if (highlight === "orange") highlight = orange;
  else if (highlight === "green") highlight = green;
  else if (highlight === "voilet") highlight = voilet;
  else if (highlight === "blue") highlight = blue;
  else if (highlight === "dark") highlight = black;
  else if (highlight === "red") highlight = red;

  let active = false;
</script>

<div class="m-5 accordian flex flex-col w-72">
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div on:click={() => active = !active} 
    class={`flex items-center justify-between h-10 border-2 border-black pl-1 pr-2 text-2xl cursor-pointer
      ${active? highlight: ''} bg-opacity-30`}>
    {title}
    {#if !active}
      <img class="w-5 h-5" src="/down-arrow.png" alt="down-arrow" />
      {:else}
      <img class="w-5 h-5 rotate-180" src="/down-arrow.png" alt="up-arrow" />
    {/if}
  </div>
  {#if active}
    <div class="pl-1 pr-1 text-xl border-2 border-t-0 border-black">{content}</div>
  {/if}
</div>

<style>
  .accordian {
    font-family: 'VT323';
  }
</style>