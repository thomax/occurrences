<script>
  export let data = []
  export let barWidth = 10
  export let barSpacing = 2

  // compute dimensions
  $: dimensions = {
    width: data.length * barWidth + (data.length - 1) * barSpacing,
    height: Math.max(...data),
  }
</script>

<!-- generate SVG -->
<svg viewBox="0 0 {dimensions.width} {dimensions.height}" xmlns="http://www.w3.org/2000/svg">
  {#each data as y, x}
    <!-- bar -->
    <rect x={x * (barWidth + barSpacing)} y={dimensions.height - y} width={barWidth} height={y} />
    <text x={4 + x * (barWidth + barSpacing)} y={Math.max(...data)} class="small">{x + 1}</text>
  {/each}
</svg>

<style>
  svg {
    background: #9ad0d9;
    padding: 1rem;
    border-radius: 0.5rem;
    overflow: visible;
  }

  rect {
    fill: #fff4;
    stroke: #fff8;
    stroke-linejoin: round;
    stroke-linecap: round;
    stroke-width: 0.5px;
  }

  .small {
    font-size: 0.2em;
  }
</style>
