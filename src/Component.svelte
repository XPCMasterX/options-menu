<script>
  import { onMount } from "svelte";

  /* Test Data for now */
  export let data;

  if (!Array.isArray(data.options)) {
    throw new Error("Options Menu: Data is not in an array format");
  }

  function loadCSSOptions(config) {
    let root = document.documentElement;
    let cssProperties = Object.entries(config);
    for (const [key, value] of cssProperties) {
      root.style.setProperty("--" + key, value.toString());
    }
  }

  onMount(() => {
    loadCSSOptions(data.css);
  });
</script>

<div class="container">
  <div class="options-menu">
    {#each data.options as option}
      <div class="option">
        <div class="input">
          <input
            type={option.type}
            min={option.min}
            max={option.max}
            value={option.start}
          />
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
  :root {
    --background-color: #fcfaf9;
  }

  .container {
    /* Remove any white space around it */
    margin-top: -1.1vh;
  }

  .options-menu {
    background-color: var(--background-color);
    color: white;
    margin-left: -0.5vw;
    width: 30vw;
    height: 94.6vh;

    padding-left: 20px;
    padding-right: 20px;
    padding-top: 20px;
  }

  .option {
    border-radius: 10px;
    background-color: #f3d3bd;
    border: solid 2px white;
    height: 7vh;
    margin-bottom: 1vh;
  }
</style>
