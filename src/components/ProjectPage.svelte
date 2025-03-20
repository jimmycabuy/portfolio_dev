<script>
  import ProjectsNavigation from './ProjectsNavigation.svelte';
  import ProgressBar from './ProgressBar.svelte';
  import { blur } from 'svelte/transition';
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';
  import { page } from '$app/stores';
  import projects from '../data/projects.json';

  export let isLoading;

  const project = $page.params.project;
  const currentProjectIndex = projects.findIndex((item) => item.route === project);
  const displayedProjects = projects.filter((project) => project.displayProject);
  const totalProjects = displayedProjects.length;
  const currentProjectDetails = projects[currentProjectIndex];
  const filteredIndex = displayedProjects.findIndex((p) => p.title === currentProjectDetails.title);
  const nextIndex = (filteredIndex + 1) % totalProjects;
  const prevIndex = (filteredIndex - 1 + totalProjects) % totalProjects;
  const nextProjectDetails = displayedProjects[nextIndex];
  const prevProjectDetails = displayedProjects[prevIndex];

  onMount(() => {
    gsap.from('.container_image', {
      y: -500,
      duration: 1,
      delay: 1.35,
      opacity: 0
    });

    gsap.from('.bloc_title, .container_one_project, .container_image_screens', {
      duration: 3,
      delay: 2.35,
      opacity: 0
    });
  });
</script>

<svelte:head>
  <title>Jimmy C. | {currentProjectDetails.title}.</title>
</svelte:head>

<ProgressBar />
<main
  class="py-6 px-12 flex justify-center items-center flex-col md:px-24 4xl:px-72"
  class:is_loading={isLoading}
  out:blur
  in:blur
>
  <div class="container_image flex justify-center">
    <div class="bloc_image">
      <img preload src={`/assets/${currentProjectDetails.src}.webp`} alt={currentProjectDetails.title} />
    </div>
  </div>
  <div class="bloc_title">
    <h1>{currentProjectDetails.title}</h1>
  </div>
  <div class="container_one_project">
    <div class="bloc_left">
      {#each currentProjectDetails.info as { label, value }}
        <div class="flex gap-12">
          <h6 class="col1">{label.toUpperCase()}</h6>
          <h6 class="col2">{value}</h6>
        </div>
      {/each}
    </div>

    <div class="bloc_right">
      <p>{currentProjectDetails.description}</p>
      {#if currentProjectDetails.showlink}
        <a href={currentProjectDetails.href} target="_blank" class="enlarged">
          <span class="enlarged view_website">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="3 0 24 20"
              stroke-width="1.5"
              stroke="currentColor"
              class="enlarged w-5 h-5"
              color="#fff"
            >
              <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 19.5l15-15m0 0H8.25m11.25 0v11.25" />
            </svg>
            <span class="enlarged">View {currentProjectDetails.type}</span>
          </span>
        </a>
      {/if}
    </div>
  </div>

  {#if currentProjectDetails.pictures}
    <div class="container_image_screens desktop">
      {#each currentProjectDetails.pictures as picture}
        <div class="bloc_image_screen">
          <img preload src="/assets/screens/{picture.includes('gif') ? picture : picture + '.webp'}" alt={picture} />
        </div>
      {/each}
    </div>
  {/if}
  {#if currentProjectDetails.picturesMobile}
    <div class="container_image_screens mobile">
      {#each currentProjectDetails.picturesMobile as picture}
        <div class="bloc_image_screen">
          <img preload src="/assets/screens/{picture}.webp" alt={picture} />
        </div>
      {/each}
    </div>
  {/if}
  <ProjectsNavigation {nextProjectDetails} {prevProjectDetails} />
</main>

<style>
  .is_loading {
    display: none;
  }
  main {
    z-index: 1;
  }

  h1 {
    margin-bottom: 2rem;
    font-size: xx-large;
    border-bottom: 2px solid #fff;
    text-transform: uppercase;
    font-weight: 700;
  }

  .container_image {
    width: 75%;
    margin-top: -7rem;
  }

  @media (min-height: 875px) {
    .container_image {
      margin-top: -7.5rem;
    }
  }

  .bloc_image {
    border-radius: 0 0 40px 40px;
    overflow: hidden;
    margin-bottom: 2rem;
  }

  .bloc_image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .container_image_screens {
    width: 75%;
  }

  .mobile {
    display: none;
  }

  .bloc_image_screen {
    border-radius: 10px;
    overflow: hidden;
    margin-bottom: 3rem;
  }

  .bloc_image_screen img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .container_one_project {
    display: flex;
    flex-direction: row;
    height: 100%;
    width: 75%;
    gap: 2rem;
  }

  .bloc_title {
    width: 75%;
  }

  .bloc_left {
    width: 50%;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .bloc_right {
    width: 50%;
  }

  p {
    text-align: justify;
    margin-bottom: 2rem;
  }

  a {
    position: relative;
    text-decoration: none;
    width: fit-content;
  }

  .col1 {
    width: 15%;
    text-align: left;
  }

  .col2 {
    width: 85%;
    text-align: right;
  }

  @media (pointer: fine) {
    a::after {
      content: '';
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 0;
      height: 2px;
      background-color: #fff;
      transition: width 0.3s ease-in-out;
    }

    a:hover::after {
      width: 100%;
    }
  }

  .view_website {
    width: fit-content;
    max-width: fit-content;
    display: inline-flex;
    margin-bottom: 2rem;
  }

  @media (max-width: 1023px) {
    .container_one_project {
      flex-direction: column;
      font-size: 90%;
    }

    .bloc_title,
    .container_image,
    .container_one_project,
    .container_image_screens {
      width: 100%;
    }

    .container_image {
      margin-top: 0;
    }

    .bloc_left {
      width: 100%;
    }

    .bloc_image {
      border-radius: 40px;
    }
    .bloc_right {
      width: 100%;
    }
    a {
      color: #fff;
    }
  }

  @media (max-width: 787px) {
    .mobile {
      display: block;
    }
    .desktop {
      display: none;
    }
  }
</style>
