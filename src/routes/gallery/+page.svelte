<script>
  import photos from "../../data/photos.json";
  import Spinner from "../../components/Spinner.svelte";
  import { onMount } from "svelte";
  import Slideshow from "../../components/Slideshow.svelte";

  let screenWidth, screenHeight;
  let photosPromise = Promise.resolve([]);

  const handleResize = () => {
    screenWidth = window.innerWidth;
  };

  const preloadImages = () => {
    const promises = photos.map((image) => {
      return new Promise((resolve, reject) => {
        const img = new Image();
        img.onload = resolve;
        img.onerror = reject;
        img.src = `../../assets/photos/${imageSide}/${image.name}.${image.extension}`;
      });
    });
    return Promise.all(promises);
  };

  $: imageSide = screenWidth < screenHeight ? "vertical" : "horizontal";

  onMount(() => {
    photosPromise = preloadImages();
    screenWidth = window.innerWidth;
    screenHeight = window.innerHeight;
  });
</script>

<svelte:head>
  <title>Jimmy C. | My pictures.</title>
</svelte:head>

<svelte:window on:resize={handleResize} />

{#await photosPromise}
  <Spinner />
{:then}
  <Slideshow bind:imageSide {photos} />
{/await}
