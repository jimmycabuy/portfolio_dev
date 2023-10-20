<script>
  import { onMount } from "svelte";
  import timeline from "../data/timeline.json";
  import { gsap } from "gsap";

  onMount(() => {
    gsap.from(".title", {
      y: -100,
      duration: 1,
      delay: 2.5,
      opacity: 0,
    });

    gsap.from(".timeline", {
      duration: 1,
      delay: 3.5,
      opacity: 0,
    });

    gsap.from(".timeline-item", {
      y: -100,
      duration: 1,
      delay: 3.5,
      stagger: 0.3,
      opacity: 0,
    });
  });
</script>

<main class="py-6 w-full mb-8">
  <h1 class="title my-10 text-5xl md:text-7xl">Timeline</h1>
  <ol class="timeline">
    {#each timeline as item}
      <li class="timeline-item">
        <span class="timeline-item-icon | filled-icon" />
        <div class="timeline-item-wrapper">
          <div class="timeline-item-description flex flex-col">
            <span class="text-2xl font-bold">{item?.title}</span>
            <span class="year text-xs">{item?.year}</span>
          </div>
          <div class="description">
            <p class="text-justify">
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
    width: 15px;
    height: 15px;
    border-radius: 50%;
    margin-left: -40px;
    margin-top: 13px;
    flex-shrink: 0;
    overflow: hidden;
  }
  .timeline-item-icon.filled-icon {
    background-color: #fff;
  }
  .timeline-item-description {
    display: flex;
    padding-top: 6px;
  }

  .year {
    color: #ff2f66;
  }

  .description {
    margin-top: 12px;
  }
  h1 {
    color: transparent;
    -webkit-text-stroke: 2px #fff;
    font-weight: 700;
  }
</style>
