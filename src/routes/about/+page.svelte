<script>
  import { onMount } from 'svelte';
  import Timeline from '../../components/Timeline.svelte';
  import { gsap } from 'gsap';
  import data from '../../data/about.json';

  const { title, description, paragraphs } = data.about;

  onMount(() => {
    gsap.from('.bloc_title', {
      y: -100,
      duration: 1,
      delay: 0.5,
      opacity: 0
    });

    if (window.innerWidth >= 767) {
      gsap.from('.bloc_image', {
        x: -500,
        duration: 1,
        opacity: 0,
        delay: 1.5
      });

      gsap.from('.bloc_text', {
        x: 500,
        duration: 1,
        opacity: 0,
        delay: 1.5
      });
    } else {
      gsap.from('.bloc', {
        y: 100,
        duration: 1,
        opacity: 0,
        delay: 1.5
      });
    }
  });
</script>

<svelte:head>
  <title>Jimmy C. | About me.</title>
</svelte:head>

<main class="flex justify-center flex-col items-center 4xl:px-72 px-10">
  <div class="bloc_title">
    <h1 class="text-5xl md:text-7xl py-6">{title}</h1>
  </div>
  <div class="flex gap-10 py-6 flex-col lg:flex-row bloc">
    <div class="w-full lg:w-1/2 bloc_image">
      <img
        src="https://www.thedailyjim.be/assets/profilepic/jimmycabuy.webp"
        alt="jimmycabuy"
        class="object-cover h-auto rounded-3xl aspect-square object-top"
      />
    </div>
    <div class="w-full flex gap-5 flex-col lg:w-1/2 bloc_text">
      <h2 class="text-2xl lg:text-4xl">{description}</h2>
      {#each paragraphs as p}
        <p class="leading-8 text-justify sm:text-left">
          {p}
        </p>
      {/each}
    </div>
  </div>
  <Timeline />
</main>

<style>
  h1 {
    color: transparent;
    -webkit-text-stroke: 2px #fff;
    font-weight: 700;
  }
</style>
