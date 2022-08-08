<script>
  const count = 20
  export let occurrences

  for (let i = 0; i < count; i++) {
    occurrences[i] = 0
  }

  const increment = (index, inc) => {
    if (inc > 0 || window.confirm('Sure you want to decrease?')) {
      occurrences[index] = occurrences[index] + inc
    }
    console.log(index, occurrences)
  }
</script>

<div class="numbersWrapper">
  <div class="item borderless">Count</div>
  <div class="item borderless">Number</div>
  <div class="borderless" />
  {#each occurrences as occurrence, index}
    <div class="item">
      {occurrence}
    </div>

    <div class="item bold">
      {index + 1}
    </div>

    <div class="borderless">
      <button on:click={() => increment(index, 1)}> + </button>
      <button on:click={() => increment(index, -1)}> - </button>
    </div>
  {/each}
</div>

<style>
  button {
    border: 1px solid rgb(185, 184, 184);
    margin-right: 5px;
  }

  .numbersWrapper {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(auto-fill, 30px);
    grid-row-gap: 0.5em;
    grid-column-gap: 0.5em;
    width: 50vw;
    max-width: 50vw;
  }

  .item {
    border: 1px solid rgb(185, 184, 184);
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .bold {
    font-size: 2em;
    font-weight: 700;
  }

  .borderless {
    border: none;
  }
</style>
