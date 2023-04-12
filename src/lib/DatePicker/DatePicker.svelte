<script>
  
  export let myDate;
</script>

<div class="date m-5 flex flex-col w-64">
  <div class="text-xl pl-1">Date</div>
  <input class="pl-1 pr-1 h-8 border-2 border-black focus:outline-none" type="date" bind:value={myDate} />
</div>

<style>
  .date {
    font-family: "VT323";
  }
</style>
