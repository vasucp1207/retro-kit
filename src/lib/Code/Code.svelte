<script>
  import Highlight from "svelte-highlight";
  import "svelte-highlight/styles/github.css";
  import typescript from "svelte-highlight/languages/typescript";
  import atomOneDark from "svelte-highlight/styles/atom-one-dark";

  export let filename = "index.ts";
  export let code = `
    import squareArea from './square';
    import circleArea from './circle';
    console.log('Area of square: ', squareArea(5));
    console.log('Area of circle', circleArea(5));
  `;
  export let bg = "bg-[#9547b7]";

  let voilet = "bg-[#9547b7]";
  let red = "bg-[#ff0000]";
  let orange = "bg-[#fc4501]";
  let green = "bg-[#92cc42]";
  let blue = "bg-[#40b3ff]";
  let black = "bg-[#212529]";

  if (bg === "orange") bg = orange;
  else if (bg === "green") bg = green;
  else if (bg === "voilet") bg = voilet;
  else if (bg === "blue") bg = blue;
  else if (bg === "dark") bg = black;
  else if (bg === "red") bg = red;

  let shadow = "";
  for (let i = 0; i < bg.length - 1; i++) {
    if (i > 3) shadow += bg[i];
  }
</script>

<svelte:head>
  {@html atomOneDark}
</svelte:head>

<div class="code m-5">
  <div class={`top h-[30px] bg-[#323232] text-white flex items-center border-b-2 border-white`}>
    <!-- <div class="dots flex gap-1 items-center m-2">
      <div class="w-3 h-3 bg-[#535353] rounded-[100px]"></div>
      <div class="w-3 h-3 bg-[#535353] rounded-[100px]"></div>
      <div class="w-3 h-3 bg-[#535353] rounded-[100px]"></div>
    </div> -->
    <span class="bg-[#212121] h-[28px] pl-2 pr-2 flex items-center">{filename}</span>
  </div>
  <div>
    <Highlight language={typescript} {code}>
    </Highlight>
  </div>
</div>

<style>
  @import url(https://fonts.googleapis.com/css?family=VT323);
  .top {
    font-family: "VT323", monospace;
    /* border-top-right-radius: 5px;
    border-top-left-radius: 5px; */
  }

  .code {
    width: 600px;
  }
  :global(.hljs) {
    /* box-shadow: 7px 7px #bc93f9; */
    font-family: "VT323", monospace;
    font-size: 20px;
    background: #212121 !important;
    /* border-end-start-radius: 5px;
    border-end-end-radius: 5px; */
  }
  :global(pre code.hljs) {
    padding: 0px !important;
  }
  :global(.hljs-keyword) {
    color: #ff79c6 !important;
  }
  :global(.hljs-string) {
    color: #f1fa8c !important;
  }
  :global(.hljs-variable) {
    color: #40b3ff !important;
  }
  :global(.hljs-number) {
    color: #40b3ff !important;
  }
  :global(.hljs-title) {
    color: #50fa7b !important;
  }
</style>
