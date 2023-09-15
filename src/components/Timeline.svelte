<script>
  import timeline from "../data/timeline.json";

  const startYear = 2015;
  const nextYear = new Date().getFullYear() + 1;
  const numberOfYear = nextYear - startYear;
</script>

<main class="px-10 xl:px-36 py-6 w-full">
  <h1 class="my-10 text-5xl md:text-7xl">Timeline</h1>
  <div
    class="grid_container"
    style="grid-template-columns: repeat({numberOfYear}, 1fr); grid-template-rows: repeat({timeline.length}, 1fr);"
  >
    {#each timeline as item}
      <div
        class="one_element"
        style="grid-area: {item.startRow} / {item.startCol} / {item.endRow} / {item.endCol};"
      >
        <h2>{item.year}</h2>
        <h2>{item.title}</h2>
      </div>
    {/each}
  </div>
</main>

<style>
  @media (min-width: 1023px) {
    .grid_container {
      display: grid;
      grid-row-gap: 1.5rem;
      width: 100%;
    }
  }

  @media (max-width: 1022px) {
    .grid_container {
      width: 100%;
      display: flex;
      gap: 1.5rem;
      flex-direction: column;
    }
  }

  h1 {
    color: transparent;
    -webkit-text-stroke: 2px #fff;
    font-weight: 700;
  }

  .one_element {
    border: 2px solid #fff;
    border-radius: 3rem;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 5rem;
    flex-direction: column;
  }
</style>
