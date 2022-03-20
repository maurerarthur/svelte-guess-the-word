<script>
  import Wordle from './Wordle.svelte';
</script>

<div class="h-100 container-fluid">
  <div class="h-100 row justify-content-center align-items-end">
    <Wordle />
    <p>This is a custom implementation using some Wordle concepts for programming purpose only.</p>
  </div>
</div>

<style>
  :root {
    --purple: #503047;
    --light-white: #D0E3C4;
  }

  * {
    font-family: "League Gothic", sans-serif;
  }

  div {
    background-color: var(--purple);
  }

  p {
    font-size: 20px;
    color: var(--light-white);
  }
</style>