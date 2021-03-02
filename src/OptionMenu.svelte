<script>
  import { onMount } from 'svelte';
  import Arrow from './Arrow.svelte';
  export let data;

  if (!Array.isArray(data.options)) {
    throw new Error('Options Menu: Data is not in an array format');
  }

  function setCSSOptions(config) {
    let root = document.documentElement;
    let cssProperties = Object.entries(config);
    for (const [key, value] of cssProperties) {
      root.style.setProperty('--' + key, value.toString());
    }
  }

  let dropdownModes = {};
  for (var option in data.options) {
    dropdownModes[option.label] = false;
  }

  onMount(() => {
    // setCSSOptions(data.css);
  });
</script>

<div class="container">
  <div class="options-menu">
    {#each data.options as option}
      <div class="option" id={option.id}>
        <div class="input">
          <div class="before-dropdown">
            <label for={option.label}>{option.label}</label>
            <div class="dropdown-container">
              <button
                class="dropdown"
                on:click={() => {
                  dropdownModes[option.id] =
                    dropdownModes[option.id] === true ? false : true;

                  dropdownModes[option.id] === true
                    ? (document.getElementById(option.id).style.height = '10vh')
                    : (document.getElementById(option.id).style.height = '5vh');

                  console.log(document.getElementById(option.id).style.height);
                }}><Arrow /></button
              >
            </div>
          </div>
          {#if dropdownModes[option.id]}
            <input
              type={option.type}
              min={option.min}
              max={option.max}
              value={option.start}
            />
          {/if}
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
  :root {
    --background-color: #fcfaf9;
    --option-height: 5vh;
  }

  .container {
    /* Remove any white space around it */
    margin-top: -1.1vh;
    display: flex;
    flex-direction: row;
  }

  .options-menu {
    background-color: var(--background-color);
    color: black;
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
    height: var(--option-height);
    margin-bottom: 1vh;
  }

  input[type='range'] {
    -webkit-appearance: none;
    width: 100%;
    background: transparent;
  }

  input[type='range']::-moz-range-thumb {
    border: none;
    height: 16px;
    width: 16px;
    border-radius: 3px;
    background: #ceb3ab;
    cursor: pointer;
  }
  input[type='range']::-webkit-slider-thumb {
    -webkit-appearance: none;
    border: none;
    height: 16px;
    width: 16px;
    border-radius: 3px;
    background: #ceb3ab;
    cursor: pointer;
    margin-top: -14px;
  }

  input[type='range']:focus {
    outline: none;
  }
  input[type='range']::-moz-range-track {
    width: 90%;
    height: 8.4px;
    cursor: pointer;
    background: #ffffff;
    border-radius: 5px;
    border: none;
  }

  label {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    flex-grow: 2;
    padding-top: 0.7vh;
    padding-left: 1vh;
  }

  .dropdown {
    background-color: transparent;
    border: none;
    transition-duration: 0.3s;
    height: 35px;
    width: 35px;
    border-radius: 50%;

    display: flex;
    flex-direction: row;
    align-items: center;
    float: right;
    flex-grow: 1;
  }
  .dropdown:hover {
    background-color: #ffffffaa;
  }

  .dropdown-container {
    padding-top: 0.11vh;
  }

  .before-dropdown {
    display: flex;
    flex-direction: row;
  }
</style>
