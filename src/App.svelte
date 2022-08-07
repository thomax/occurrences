<script>
  import svelteLogo from './assets/svelte.svg'
  import Counter from './lib/Counter.svelte'
</script>

<main>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/d20.png" class="logo" alt="d20" />
    </a>
  </div>
  <h1>Dat wonky d20</h1>

  <div class="card">
    <Counter />
  </div>
</main>

<style>
  .logo {
    height: 12em;
    padding: 1em;
    will-change: filter;
    transform: rotate(114deg);
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #47972caa);
  }
</style>
