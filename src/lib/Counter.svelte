<script>
  export let occurrences
  export let dieSides

  for (let i = 0; i < dieSides; i++) {
    occurrences[i] = 0
  }

  const increment = (index, inc) => {
    if (inc > 0 || window.confirm('Just checking you really want to decrease..?')) {
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
    border-radius: 8px;
    padding: 0.6rem 1rem;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.25s;
  }

  button:hover {
    background-color: #51a618;
  }
  button:focus,
  button:focus-visible {
    outline: 4px auto -webkit-focus-ring-color;
  }

  .numbersWrapper {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(auto-fill, 30px);
    grid-row-gap: 0.5rem;
    grid-column-gap: 0.5rem;
  }

  .item {
    border: 1px solid rgb(185, 184, 184);
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 8vw;
  }

  .bold {
    font-size: 1.5rem;
    font-weight: 700;
  }

  .borderless {
    border: none;
  }
</style>
