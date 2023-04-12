<script>

  export let listItem = []
</script>

<div class="m-5 list-cont">
  <ol>
    {#each listItem as item}
      <li class="items relative text-xl">{item.text}</li>
    {/each}
  </ol>
</div>

<style>
  .list-cont {
    font-family: 'VT323';
  }
  .items:before {
    position: absolute;
    content: '';
    width: 6px;
    height: 6px;
    background: black;
    display: block;
    top: 45%;
    left: -1%;
  }
</style>