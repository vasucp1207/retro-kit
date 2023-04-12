<script>
  import { onMount } from 'svelte';
  
  let text = 'Hello, world!';
  let typedText = '';
  let typingSpeed = 100;
  
  onMount(() => {
    const intervalId = setInterval(() => {
      if (text.length > typedText.length) {
        typedText += text[typedText.length];
      }
      else {
        clearInterval(intervalId);
      }
    }, typingSpeed);
  });
</script>

<p class="m-5 typing text-2xl">{typedText}</p>

<style>
  .typing {
    font-family: "VT323", monospace;
  }
</style>
