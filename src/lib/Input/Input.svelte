<script>
  export let border = "border-[#9547b7]";
  export let name = "";
  export let number = 0;
  export let type = "";
  export let placeholder = "";
  export let label = "";

  let voilet = "border-[#9547b7]";
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

<div class="input relative mt-5 ml-5 flex w-fit">
  {#if label !== ""}
    <span class="bg-white absolute z-10 -top-4 pl-1 pr-1 left-2 text-xl"
      >{label}
      </span>
  {/if}

  <span class="absolute w-1 h-1 bg-white -top-[2px] -left-[2px]" />
  <span class="absolute w-1 h-1 bg-white -top-[2px] -right-[2px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[2px] -left-[2px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[2px] -right-[2px]" />

  {#if type === ""}
    <input
      type="text"
      bind:value={name}
      class={`border-2 ${border} border-opacity-60 focus:outline-none focus:${border}
  p-1 w-80 h-12 ease-in duration-100`}
      {placeholder}
    />
  {:else if type === "number"}
    <input
      type="number"
      bind:value={number}
      class={`border-2 ${border} border-opacity-60 focus:outline-none focus:${border}
  p-1 w-80 h-12 ease-in duration-100`}
      {placeholder}
    />
  {/if}
</div>

<style>
  .input {
    font-family: "VT323", monospace;
    height: 48px !important;
  }
  input {
    font-size: 20px;
    box-shadow: 2px 2px var(border);
  }
  input:focus {
    box-shadow: 4px 4px var(border);
    /* box-shadow: 4px 4px #e37956; */
  }
</style>
