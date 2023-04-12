# Retro Kit
## Buils retro styled svelte apps

## 📦Installation
```bash
npm i retro-kit
```

## ☃️Usage
```svelte
<script> 
  import { Button, Code } from 'retro-kit';

  const handleClick = () => {
    alert("click me");
  };

  let filename = "retro.ts";
  let code = `
    import squareArea from './square';
    import circleArea from './circle';
    console.log('Area of square: ', squareArea(5));
    console.log('Area of circle', circleArea(5));
  `;

</script>

<Button on:click={handleClick} bg="orange">Click Me</Button>

<Code {filename} {code} />
```
