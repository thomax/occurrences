<script>
  export let data = []
  const barWidth = 20
  const barSpacing = 5
  const barYOffset = 2

  // compute dimensions
  $: dimensions = {
    width: data.length * barWidth + (data.length - 1) * barSpacing,
    height: Math.max(...data),
  }
</script>

<!-- generate SVG -->
<svg width={dimensions.width} height={dimensions.height} xmlns="http://www.w3.org/2000/svg">
  {#each data as y, x}
    <!-- bar -->
    <rect
      x={x * (barWidth + barSpacing)}
      y={dimensions.height - y + barYOffset}
      width={barWidth}
      height={y}
    />
    <!-- calculate x-placement of text depending on one or two digits in number -->
    <text x={(x < 9 ? 6 : 3) + x * (barWidth + barSpacing)} y={Math.max(...data)} class="small"
      >{x + 1}</text
    >
  {/each}
</svg>

<style>
  svg {
    background: #51a618;
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
    font-size: 0.8rem;
  }
</style>
