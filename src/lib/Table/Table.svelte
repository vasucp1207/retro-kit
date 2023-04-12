<script>
  export let columns = [];
  export let data = [];

  export let highlight = "hover:bg-[#9547b7]";

  let voilet = "hover:bg-[#9547b7]";
  let lightVoilet = "hover:bg-[#bc93f9]";
  let red = "hover:bg-[#ff0000]";
  let orange = "hover:bg-[#fc4501]";
  let green = "hover:bg-[#92cc42]";
  let blue = "hover:bg-[#40b3ff]";
  let black = "hover:bg-[#212529]";

  if (highlight === "orange") highlight = orange;
  else if (highlight === "green") highlight = green;
  else if (highlight === "voilet") highlight = voilet;
  else if (highlight === "blue") highlight = blue;
  else if (highlight === "dark") highlight = black;
  else if (highlight === "red") highlight = red;

</script>

<table class="relative m-5 table text-2xl">
  <tr class="bg-[#d3d3d3]">
    {#each columns as column}
      <th class="border-2 border-black">{column.header}</th>
    {/each}
  </tr>
  {#each data as row}
    <tr class={`${highlight} hover:bg-opacity-30`}>
      <td class="border-2 border-black text-center pl-2 pr-2">{row.name}</td>
      <td class="border-2 border-black text-center pl-2 pr-2">{row.age}</td>
      <td class="border-2 border-black text-center pl-2 pr-2">{row.email}</td>
    </tr>
  {/each}

  <span class="absolute w-1 h-1 bg-white -top-[2.5px] -left-[2.5px]" />
  <span class="absolute w-1 h-1 bg-white -top-[2.5px] -right-[2.5px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[1.6px] -left-[2px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[2px] -right-[2px]" />
</table>

<style>
  .table {
    font-family: "VT323";
  }
</style>
