<script>
  import Counter from './lib/Counter.svelte'
  import BarChart from './lib/BarChart.svelte'
  const dieSides = 20

  window.onbeforeunload = () => {
    return 'Are you sure you want to leave?'
  }

  $: occurrences = []
</script>

<main class="mainWrapper">
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/d20.png" class="logo" alt="d20" />
    </a>
  </div>

  <h1>Dat wonky d{dieSides}</h1>

  <div class="counterWrapper">
    <Counter bind:occurrences {dieSides} />
  </div>

  <div class="chartWrapper">
    <BarChart data={occurrences} />
  </div>

  <div class="dataWrapper">
    {JSON.stringify(occurrences, null, 2)}
  </div>
</main>

<style>
  .logo {
    height: 12em;
    will-change: filter;
    transform: rotate(114deg);
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #47972caa);
  }

  .mainWrapper {
    min-width: 50vw;
    max-width: 800px;
  }

  .counterWrapper {
    padding: 0;
    min-width: 30vw;
    max-width: 400px;
    margin: 0 auto;
  }

  .chartWrapper {
    margin-top: 1rem;
  }

  .dataWrapper {
    margin-top: 1em;
  }
</style>
