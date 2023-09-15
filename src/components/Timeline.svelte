<script>
  import timeline from "../data/timeline.json";
</script>

<main class="px-10 xl:px-36 py-6 w-full">
  <h1 class="my-10 text-5xl md:text-7xl">Timeline</h1>
  <ol class="timeline">
    {#each timeline as item}
      <li class="timeline-item">
        <span class="timeline-item-icon | filled-icon">
          <svg
            width="24"
            height="24"
            viewBox={item?.viewbox}
            xmlns="http://www.w3.org/2000/svg"
          >
            <path fill="#ff2f66" d={item?.d} />
          </svg>
        </span>
        <div class="timeline-item-wrapper">
          <div class="timeline-item-description">
            <span>{item?.year} > {item?.title}</span>
          </div>
          <div class="comment">
            <p class="md:text-justify">
              {item?.description}
            </p>
          </div>
        </div>
      </li>
    {/each}
  </ol>
</main>

<style>
  .timeline {
    width: 100%;
    display: flex;
    flex-direction: column;
    padding: 32px 0 32px 32px;
    border-left: 2px solid #fff;
    gap: 2rem;
  }
  .timeline-item {
    display: flex;
    gap: 24px;
  }

  .timeline-item-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin-left: -52px;
    flex-shrink: 0;
    overflow: hidden;
  }
  .timeline-item-icon svg {
    width: 20px;
    height: 20px;
  }
  .timeline-item-icon.filled-icon {
    background-color: #fff;
  }
  .timeline-item-description {
    display: flex;
    padding-top: 6px;
  }

  .comment {
    margin-top: 12px;
    border-radius: 6px;
  }
  h1 {
    color: transparent;
    -webkit-text-stroke: 2px #fff;
    font-weight: 700;
  }
</style>
