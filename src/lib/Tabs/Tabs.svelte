<script>
  
  export let tabs = []
  export let highlight = "bg-[#9547b7]";
  
  let active = 0;

  let voilet = "bg-[#9547b7]";
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

  let color = "";
  for(let i = 3; i < highlight.length; i++) {
    color += highlight[i];
  }
  let border = "border-" + color;

</script>

<div class="relative tabs flex w-fit m-5 flex-col border-2 border-black">
  <div>
    {#each tabs as tab, index}
      <button 
        on:click={() => active = index} 
        class={`h-10 border-b-2 text-2xl w-24 ${index === active? border: ''} 
          ${index === active? 'bg-opacity-30': ''} ${index === active? highlight: ''}`}>
        {tab.title}
      </button>
    {/each}
  </div>

  <div class="text-xl min-h-[160px] p-1">
    {tabs[active].content}
  </div>

  <span class="absolute w-1 h-1 bg-white -top-[3.5px] -left-[3.5px]" />
  <span class="absolute w-1 h-1 bg-white -top-[3.5px] -right-[3.5px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[3.5px] -left-[3.5px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[3.5px] -right-[3.5px]" />
</div>

<style>
  .tabs {
    font-family: 'VT323';
  }
</style>