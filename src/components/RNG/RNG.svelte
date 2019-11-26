<script>
  export let sides = 6;
  export let numOfDice = 1;
  export let rolls = 1;
  export let results = [];
  let resultTotal = null;

  function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  function resultsReducer(accumulator, currentValue) {
    return accumulator + currentValue;
  }

  function roller(sides, numOfDice, rolls) {
    results = [];
    for (let i = 0; i < rolls; i++) {
      for (let n = 0; n < numOfDice; n++) {
        let rollResult = 0;
        rollResult = getRandomInt(1, sides);
        results.push(rollResult);
      }
    }
    resultTotal = results.reduce(resultsReducer);
  }
</script>

<style>
  .rolls {
    display: flex;
  }
  .result,
  .total {
    background: #faf9f4;
    border: 1px solid #ccc;
    width: 28px;
    height: 28px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 3px;
    margin-right: 4px;
  }
  .total {
    background: #222;
    color: #e8d785;
    border: 1px solid #000;
  }
</style>

<p>
  <label for="">Sides:</label>
  <input type="text" bind:value={sides} />
</p>
<p>
  <label for="">Number of Dice:</label>
  <input type="text" bind:value={numOfDice} />
</p>
<p>
  <label for="">Rolls:</label>
  <input type="text" bind:value={rolls} />
</p>

<button on:click={() => roller(sides, numOfDice, rolls)}>Roll</button>
<div class="rolls">
  {#each results as result}
    <div class="result">{result}</div>
  {/each}
  <div class="total">{resultTotal}</div>
</div>
