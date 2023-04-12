<script>
  import Image from "$lib/Image/Image.svelte";

// @ts-nocheck
  export let slides = [];

  let active = 0;

  function incActive() {
    active++;
    active %= slides.length;
  }

  function decActive() {
    active--;
    if(active < 0) active = slides.length - 1;
    active %= slides.length;
  }
</script>

<div class="relative m-5 w-1/2 h-96 bg-black">
  <div
    class="absolute bottom-3 flex w-full justify-center items-center flex-row"
  >
    {#each slides as slide, index}
      <button
        on:click={() => (active = index)}
        class={`bottom-2 w-10 h-1 bg-white ml-1 mr-1 bg-opacity-30 ${active === index? 'bg-opacity-90': ''}`}
      />
    {/each}
  </div>
    
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div on:click={decActive} class="h-full absolute w-fit flex items-center">
    <div
      class="bg-white bg-opacity-30 w-8 h-8 flex justify-center items-center absolute left-2 cursor-pointer
      text-white rounded-full hover:bg-opacity-50 hover:scale-110 transition ease-in-out"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24px"
        height="24px"
        viewBox="0 0 24 24"
        fill="currentColor"
        ><path
          fill="currentColor"
          d="M20,11V13H8L13.5,18.5L12.08,19.92L4.16,12L12.08,4.08L13.5,5.5L8,11H20Z"
        /></svg
      >
    </div>
  </div>

  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div on:click={incActive} class="h-full absolute right-0 w-fit flex items-center">
    <div
      class="bg-white bg-opacity-30 w-8 h-8 flex justify-center items-center absolute right-2 cursor-pointer
    text-white rounded-full hover:bg-opacity-50 hover:scale-110 transition ease-in-out"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24px"
        height="24px"
        viewBox="0 0 24 24"
        fill="currentColor"
        ><path
          fill="currentColor"
          d="M4,11V13H16L10.5,18.5L11.92,19.92L19.84,12L11.92,4.08L10.5,5.5L16,11H4Z"
        /></svg
      >
    </div>
  </div>

  <Image src={slides[active].src} slide />
</div>

<style>
</style>
