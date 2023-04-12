<script>

  export let message = "";
  export let placeholder = "write your message";
  export let border = "border-[#9547b7]";
  export let label = ""

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

<div class="textarea relative ml-5 mt-5 flex w-fit">
  {#if label !== ""}
    <span class="bg-white absolute -top-4 pl-1 pr-1 left-2 text-xl z-10"
    >{label}
    </span>
  {/if}
  <textarea 
    class={`relative border-2 ${border} border-opacity-60 w-96 text-xl
    focus:outline-none focus:${border} p-1 w-96`}
    bind:value={message} placeholder={placeholder}
  ></textarea>
  <span class="absolute w-1 h-1 bg-white -top-[2px] -left-[2px]" />
  <span class="absolute w-1 h-1 bg-white -top-[2px] -right-[2px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[2px] -left-[2px]" />
  <span class="absolute w-1 h-1 bg-white -bottom-[2px] -right-[2px]" />
</div>

<style>
  .textarea {
    font-family: 'VT323';
  }
  .textarea {
    /* box-shadow: 3px 3px #bc93f9; */
  }
  .textarea:focus {
    /* box-shadow: 5px 5px #9547b7; */
  }
</style>