<script>

  export let swVal = "left";

  let pos = "left-[2px]";
  let bg = "bg-[#e4e6ea]";
  function handleClick() {
    if(swVal === "left") {
      swVal = "right";
      pos = "right-[2px]";
      bg = "bg-blue-500";
    } else {
      swVal = "left";
      pos = "left-[2px]";
      bg = "bg-[#e4e6ea]";
    }
  }
</script>

<div class="m-5 flex w-fit">
  <button
    on:click={handleClick}
    class={`relative ${bg} w-11 h-[26px] rounded-full p-[2px] flex items-center border-[1px] border-[#dddddd]`}>
    <div class={`absolute bg-white h-5 w-5 rounded-[50%] shadow-lg ${pos} ease-in-out`}></div>
  </button>
</div>

<style>

</style>