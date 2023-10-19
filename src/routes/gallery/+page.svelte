<script>
  import photos from "../../data/photos.json";
  import { onMount } from "svelte";
  import { gsap } from "gsap";

  let main;

  const uniquePictures = new Set();

  while (uniquePictures.size < 60) {
    const randomIndex = Math.floor(Math.random() * photos.length);
    uniquePictures.add(photos[randomIndex]);
  }

  const randomPictures = Array.from(uniquePictures);

  $: if (main) {
    gsap.from(".box", {
      y: 100,
      duration: 1,
      stagger: 0.2,
      delay: 1,
      opacity: 0,
    });
  }
  onMount(() => {
    main = document.querySelector("main");
  });
</script>

<main class="px-12 4xl:px-72">
  <div class="auto-grid">
    {#each randomPictures as photo}
      <div class="box">
        <img
          src={`../../assets/photos/${photo.folder}/${photo.name}.webp`}
          alt={photo.name}
          width="100%"
          height="100%"
          preload
          class="object-cover aspect-square"
        />
      </div>
    {/each}
  </div>
</main>

<style>
  .auto-grid {
    --auto-grid-min-size: 16rem;
    display: grid;
    grid-template-columns: repeat(
      auto-fill,
      minmax(var(--auto-grid-min-size), 1fr)
    );
    grid-gap: 2rem;
  }
</style>
