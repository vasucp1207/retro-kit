<script>
  import Image from "$lib/Image/Image.svelte";

  export let title = "Title";
  export let subtitle = "Subtitle";
  export let description = "Description";
  export let img = "";
  export let atLink = "";
  export let border = "border-[#9547b7]";

  let mouseover = false;

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

  let shadow = "";
  for(let i = 8; i < border.length - 1; i++) {
    shadow += border[i];
  }

  let hoverBg = `hover:bg-[${shadow}]`;
</script>

<div
  on:mousemove={() => mouseover = true}
  on:mouseleave={() => mouseover = false}
  class={`card border-2 ${border} overflow-hidden border-opacity-70 w-96 min-h-full m-5 hover:${border} hover:bg-opacity-100`}
>
  <div class="text-4xl m-2">
    {title}
  </div>
  <div class="text-2xl m-2 mt-0 mb-0">
    {subtitle}
  </div>
  <div class="mt-4 mb-4 flex justify-center">
    <Image src={img} />
  </div>
  <div class="text-xl m-2 mt-0 mb-0">
    {description}
  </div>
  <a class={`text-xl p-2 underline border-opacity-70 ${hoverBg} hover:bg-opacity-30`} href={atLink}>Link</a>
</div>

<style>
  .card {
    font-family: "VT323", monospace;
    /* box-shadow: 5px 5px #bc93f9; */
  }
  .card:hover {
    /* box-shadow: 7px 7px #9547b7; */
  }
</style>
