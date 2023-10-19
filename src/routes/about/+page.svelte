<script>
  import { onMount } from "svelte";
  import Timeline from "../../components/Timeline.svelte";
  import { gsap } from "gsap";

  onMount(() => {
    gsap.from(".bloc_title", {
      y: -100,
      duration: 1,
      delay: 0.5,
      opacity: 0,
    });

    if (window.innerWidth >= 767) {
      gsap.from(".bloc_image", {
        x: -500,
        duration: 1,
        opacity: 0,
        delay: 1.5,
      });

      gsap.from(".bloc_text", {
        x: 500,
        duration: 1,
        opacity: 0,
        delay: 1.5,
      });
    } else {
      gsap.from(".bloc", {
        y: 100,
        duration: 1,
        opacity: 0,
        delay: 1.5,
      });
    }
  });
</script>

<svelte:head>
  <title>Jimmy C. | About me.</title>
</svelte:head>

<main class="flex justify-center flex-col items-center 4xl:px-72 px-10">
  <div class="bloc_title">
    <h1 class="text-5xl md:text-7xl py-6">I'm Jimmy.</h1>
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
      <h2 class="text-2xl lg:text-4xl">
        I'm a front-end developer & photographer working in sunny Brussels,
        Belgium.
      </h2>

      <p class="leading-8 text-justify sm:text-left">
        I graduated with a degree in e-business from EPHEC and spent over 2
        years at a digital marketing agency as a content creator, social ads
        expert, and social media manager. I then traveled the world for 6
        months, capturing unique moments and landscapes as a photographer. I
        expanded my technical skills with an intensive JavaScript Bootcamp and
        became a front-end developer at Decathlon Belgium, combining my diverse
        experiences to create exceptional web experiences.
      </p>
      <p class="leading-8 text-justify sm:text-left">
        My journey has shaped me into a curious and creative professional,
        always seeking new challenges and pushing my skills to the limit.
      </p>
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
