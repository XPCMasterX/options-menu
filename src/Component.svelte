<script>
  export let data;
</script>

<div class="container">
  <div class="options-menu">
    <div class="option">
      <input class="slider" type="range" min="0" max="100" />
    </div>
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

    padding: 20px;
  }

  .option {
    border-radius: 10px;
    background-color: #f3d3bd;
    border: solid 2px white;
    height: 5vh;
  }
</style>
