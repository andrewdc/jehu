<script>
  import Board from "./Board/Board.svelte";
  import RNG from "./RNG/RNG.svelte";
</script>

<style>
  .screen {
    margin: 0 auto;
    width: 50vw;
  }
  h1 {
    text-align: center;
  }
</style>

<h1>The Adventures of Jehu</h1>
<RNG />
<div class="screen">
  <Board />
</div>
