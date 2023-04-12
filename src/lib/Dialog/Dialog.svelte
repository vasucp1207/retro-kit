<!-- Dialog.svelte -->
<script>
  import Button from "../Button/Button.svelte";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let visible = false;
  export let border = "border-[#161a1c]";

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
  
  function close() {
    dispatch("click");
  }
</script>

<div class="dialog text-2xl">
  {#if visible}
    <div class="fixed top-0 left-0 w-full h-full bg-black opacity-50 z-20" />
    <div
      class={`fixed top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 z-30 bg-white shadow-lg p-6 border-2 ${border} border-opacity-70`}
    >
      <slot name="title">
        <h2 class="text-2xl font-bold mb-4">No title is privided</h2>
      </slot>

      <slot name="description" />

      <div class="flex justify-center">
        <Button on:click={close} bg="orange" outlined>Cancel</Button>
      </div>
    </div>
  {/if}
</div>

<style>
  .dialog {
    font-family: "VT323", monospace;
  }
</style>
