<script>
  import photos from "../../data/photos.json";
  import { onMount } from "svelte";

  let currentIndex = 0;
  let paused = false;
  let interval;
  let imageSide;
  let screenWidth = window.innerWidth;

  const handleSlideshow = (event) => {
    if (event.target.classList.contains("slide")) {
      paused = !paused;
    }
  };

  const handleResize = () => {
    screenWidth = window.innerWidth;
  };

  $: if (screenWidth <= 768) {
    imageSide = "vertical";
  } else {
    imageSide = "horizontal";
  }

  onMount(() => {
    document.addEventListener("mousedown", handleSlideshow);
    document.addEventListener("mouseup", handleSlideshow);
    document.addEventListener("touchstart", handleSlideshow);
    document.addEventListener("touchend", handleSlideshow);

    interval = setInterval(() => {
      if (!paused) {
        currentIndex = (currentIndex + 1) % photos.length;
      }
    }, 350);

    return () => {
      clearInterval(interval);
      document.removeEventListener("mousedown", handleSlideshow);
      document.removeEventListener("mouseup", handleSlideshow);
      document.removeEventListener("touchstart", handleSlideshow);
      document.removeEventListener("touchend", handleSlideshow);
    };
  });
</script>

<svelte:window on:resize={handleResize} />

<main class="px-12 4xl:px-72">
  <article class="slideshow">
    {#each photos as image, i}
      <div class="slide {i === currentIndex ? 'active' : ''}">
        <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
        <img
          alt={image.alt}
          on:mousedown={handleSlideshow}
          on:mouseup={handleSlideshow}
          on:touchstart={handleSlideshow}
          on:touchend={handleSlideshow}
          src={`../../assets/photos/${imageSide}/${image.name}.${image.extension}`}
        />
        {#if paused && i === currentIndex}
          <div class="description">
            <p class="description_text">
              {image.place},
            </p>
            <p class="description_text">
              {image.country}.
            </p>
          </div>
        {/if}
      </div>
    {/each}
  </article>
</main>

<style>
  .slideshow {
    position: relative;
    width: 100%;
    height: 75vh;
    margin: auto;
  }

  .slide {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 20px;
  }

  .slide:hover {
    cursor: pointer;
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
    .slideshow {
      height: 70vh;
    }
  }
</style>
