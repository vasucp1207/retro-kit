<script>
  export let text = "this is a checkbox";
  export let checked = false;
  export let bg = "#9547b7";

  let voilet = "#9547b7";
  let lightVoilet = "#bc93f9";
  let red = "#ff0000";
  let orange = "#fc4501";
  let green = "#92cc42";
  let blue = "#40b3ff";
  let black = "#212529";

  if (bg === "orange") bg = orange;
  else if (bg === "green") bg = green;
  else if (bg === "voilet") bg = voilet;
  else if (bg === "blue") bg = blue;
  else if (bg === "dark") bg = black;
  else if (bg === "red") bg = red;
</script>

<div class="checkbox m-5 flex gap-2 items-center text-2xl">
  <div class="border-2 border-black flex">
    <input
      style="background-color: {checked? bg : '#d3d3d3'}"
      class="my-checkbox cursor-pointer" type="checkbox" bind:checked 
    />
  </div>
  <span>{text}</span>
</div>

<style>
  .checkbox {
    font-family: "VT323", monospace;
  }
  .checkbox input[type="checkbox"] {
    width: 18px;
    height: 18px;
  }
  input[type="checkbox"]:checked {
    color: white;
  }
  input[type="checkbox"] {
    cursor: pointer;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    outline: 0;
    background: lightgray;
    height: 18px;
    width: 18px;
    border: 1px solid white;
    color: white;
  }

  input[type="checkbox"]:after {
    content: "";
    position: relative;
    left: 40%;
    top: 10%;
    width: 25%;
    height: 60%;
    border: solid #fff;
    border-width: 0 2px 2px 0;
    transform: rotate(50deg);
    display: none;
  }

  input[type="checkbox"]:checked:after {
    display: block;
  }
</style>
