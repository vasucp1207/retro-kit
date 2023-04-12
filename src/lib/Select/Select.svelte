<script>
  export let options = [];
  export let select = "";
  export let border = "border-[#9547b7]";
  export let label = "";

  let voilet = "border-[#9547b7]";
  let lightVoilet = "border-[#bc93f9]";
  let red = "border-[#ff0000]";
  let orange = "border-[#fc4501]";
  let green = "border-[#92cc42]";
  let blue = "border-[#40b3ff]";
  let black = "border-[#212529]";

  if (border === "orange") border = orange;
  else if (border === "green") border = green;
  else if (border === "voilet") border = voilet;
  else if (border === "blue") border = blue;
  else if (border === "dark") border = black;
  else if (border === "red") border = red;
</script>

<div class="select relative ml-5 mt-5 flex w-fit">
  {#if label !== ""}
    <span class="bg-white absolute -top-4 pl-1 pr-1 left-2 text-xl"
      >{label}
    </span>
  {/if}
  <select
    bind:value={select}
    class={`border-2 ${border} border-opacity-60 w-96 text-xl
  focus:outline-none focus:${border} p-1`}
  >
    {#each options as option}
      <option value={option}>
        {option.text}
      </option>
    {/each}
  </select>
</div>

<style>
  .select {
    font-family: "VT323";
  }
</style>
