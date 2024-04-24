<script>
  import { onMount } from "svelte";
  import { gsap } from "gsap";
  import projectsJSON from "../../data/projects.json";
  import { blur } from "svelte/transition";
  import ProjectLine from "../../components/ProjectLine.svelte";

  let currentProject = null;

  const setProject = ({ detail }) => {
    currentProject = detail;
  };

  onMount(() => {
    gsap.from(".link", {
      y: 100,
      duration: 1,
      stagger: 0.3,
      delay: 0.5,
      opacity: 0,
    });
  });
</script>

<svelte:head>
  <title>Jimmy C. | My Work.</title>
</svelte:head>

<main class="px-12 flex justify-center items-center 4xl:px-72" in:blur>
  <div class="container_projects">
    <div class="bloc_left">
      {#each projectsJSON as project}
        <ProjectLine {project} on:project={setProject} />
      {/each}
    </div>
    <div class="bloc_right">
      {#if currentProject}
        <img
          src={`/assets/${currentProject.src}.webp`}
          alt={currentProject.alt}
          class="w-full h-full object-cover rounded-xl"
        />
      {/if}
    </div>
  </div>
</main>

<style>
  main {
    overflow: hidden;
    z-index: 1;
  }

  .container_projects {
    display: flex;
    align-items: center;
    flex-direction: row;
    width: 100vw;
    gap: 1rem;
  }

  .bloc_left {
    width: 50%;
    display: flex;
    justify-content: center;
    flex-direction: column;
  }

  .bloc_right {
    display: flex;
    flex-direction: column;
    width: 50%;
  }

  @media (max-width: 1023px) or (pointer: coarse) {
    .bloc_right {
      display: none;
    }
    .bloc_left {
      width: 100%;
      padding: 0;
    }
  }
</style>
