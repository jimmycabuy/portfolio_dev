<script>
  import { onMount } from "svelte";

  export let imageSide;
  export let photos;

  let paused = false;
  let currentIndex = 0;
  let interval;

  const handleSlideshow = (event) => {
    if (
      (event.button === 0 || navigator.maxTouchPoints > 0) &&
      (event.target.classList.contains("slide") ||
        event.target.classList.contains("description") ||
        event.target.classList.contains("description_text"))
    ) {
      paused = !paused;
    }
  };

  onMount(() => {
    document.addEventListener("mousedown", handleSlideshow);
    document.addEventListener("mouseup", handleSlideshow);
    document.addEventListener("touchstart", handleSlideshow);
    document.addEventListener("touchend", handleSlideshow);

    interval = setInterval(() => {
      if (!paused) {
        currentIndex = (currentIndex + 1) % photos.length;
      }
    }, 450);

    return () => {
      clearInterval(interval);
      document.removeEventListener("mousedown", handleSlideshow);
      document.removeEventListener("mouseup", handleSlideshow);
      document.removeEventListener("touchstart", handleSlideshow);
      document.removeEventListener("touchend", handleSlideshow);
    };
  });
</script>

<article class="slideshow">
  {#each photos as { name, country, place, extension }, i}
    <div class="slide {i === currentIndex ? 'active' : ''}">
      <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
      <img
        src={`../../assets/photos/${imageSide}/${name}.${extension}`}
        alt={name}
        on:mousedown={handleSlideshow}
        on:mouseup={handleSlideshow}
        on:touchstart={handleSlideshow}
        on:touchend={handleSlideshow}
      />
      {#if paused && i === currentIndex}
        <div class="description">
          <p class="description_text">
            {place},
          </p>
          <p class="description_text">
            {country}.
          </p>
        </div>
      {/if}
    </div>
  {/each}
</article>

<style>
  .slideshow {
    position: fixed;
    width: 100vw;
    top: 0;
    bottom: 0;
  }

  .slide {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .slide.active {
    opacity: 1;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    pointer-events: none;
  }

  .description {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    color: white;
    text-align: center;
    opacity: 1;
    z-index: 999;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .description_text {
    padding: 0 2rem;
    font-size: xx-large;
    text-transform: uppercase;
  }

  @media (width <= 768px) {
    .description_text {
      font-size: x-large;
    }
  }
</style>
