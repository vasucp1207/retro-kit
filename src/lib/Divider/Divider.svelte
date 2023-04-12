<script>

  export let text = "";
</script>

<div 
  class="divider m-5 text-xl flex justify-center items-center after:content-['']
   after:bg-black after:block after:w-[100%] after:h-[2px] before:content-['']
   before:bg-black before:block before:w-[100%] before:h-[2px]">
   {#if text !== ""}
    <div class="pl-1 pr-1">{text}</div>
   {/if}
</div>

<style>
  .divider {
    font-family: 'VT323';
  }
</style>