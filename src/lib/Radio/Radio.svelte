<script>
  export let radio = 0;
  export let radioOpt = [];
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
</script>

<div class="flex flex-col m-5">
  {#each radioOpt as opt}
    <label class="radio text-xl max-w-fit flex items-center gap-2">
      <span
        class="relative h-5 w-5 border-2 border-black rounded-[50%] flex justify-center items-center"
      >
        <input
          style="background-color: {radio === opt.id ? bg : '#d3d3d3'}"
          type="radio"
          bind:group={radio}
          value={opt.id}
        />

        <span class="absolute w-1 h-1 bg-white -top-[2px] -left-[2px]" />
        <span class="absolute w-1 h-1 bg-white -top-[2px] -right-[2px]" />
        <span
          class="absolute w-1 h-1 bg-white -bottom-[2px] -left-[2px]"
        />
        <span
          class="absolute w-1 h-1 bg-white -bottom-[2px] -right-[2px]"
        />
      </span>
      {opt.text}
    </label>
  {/each}
</div>

<style>
  :global(input:checked) {
    background: var(--bg);
  }
  .radio {
    font-family: "VT323";
  }
  input[type="radio"]:checked {
    color: white;
  }
  input[type="radio"] {
    cursor: pointer;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    outline: 0;
    background: lightgray;
    height: 16px;
    width: 16px;
    border-radius: 50%;
    border: 1px solid white;
    color: white;
  }
</style>
