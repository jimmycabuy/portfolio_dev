<script>
  import ProjectsNavigation from "../../../components/ProjectsNavigation.svelte";
  import ProgressBar from "../../../components/ProgressBar.svelte";
  import { page } from "$app/stores";
  import projectsJSON from "../../../data/projects.json";
  import { blur } from "svelte/transition";
  import Spinner from "../../../components/Spinner.svelte";

  let isLoading = true;

  setTimeout(() => {
    isLoading = false;
  }, 1500);

  const project = $page.params.project;
  const currentIndex = projectsJSON.findIndex((item) => item.route === project);
  const subProjectDetails = projectsJSON[currentIndex];
  const nextProject =
    currentIndex + 1 < projectsJSON.length
      ? projectsJSON[currentIndex + 1]
      : projectsJSON[0];
  const prevProject =
    currentIndex - 1 >= 0
      ? projectsJSON[currentIndex - 1]
      : projectsJSON[projectsJSON.length - 1];
</script>

<svelte:head>
  <title>Jimmy C. | My Work. | {subProjectDetails.title}.</title>
</svelte:head>

{#if isLoading}
  <Spinner />
{/if}

<ProgressBar />
<main
  class="py-6 px-12 flex justify-center items-center flex-col md:px-24 4xl:px-72"
  class:is_loading={isLoading}
  out:blur
  in:blur
>
  <div class="container_image flex justify-center">
    <div class="bloc_image">
      <img
        preload
        src={`/assets/${subProjectDetails.src}.webp`}
        alt={subProjectDetails.title}
      />
    </div>
  </div>
  <div class="bloc_title">
    <h1>{subProjectDetails.title}</h1>
  </div>
  <div class="container_one_project">
    <div class="bloc_left">
      <div class="flex gap-12">
        <h6 class="col1">CATEGORY</h6>
        <h6 class="col2">{subProjectDetails.subtitle}</h6>
      </div>
      <div class="flex gap-12">
        <h6 class="col1">YEAR</h6>
        <h6 class="col2">{subProjectDetails.year}</h6>
      </div>
      <div class="flex gap-12">
        <h6 class="col1">TECHNO</h6>
        <h6 class="col2">{subProjectDetails.techno}</h6>
      </div>
    </div>

    <div class="bloc_right">
      <p>{subProjectDetails.description}</p>
      <a href={subProjectDetails.href} target="_blank">
        <span class="view_website">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="3 0 24 20"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-5 h-5 svg_view_website"
            color="#fff"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4.5 19.5l15-15m0 0H8.25m11.25 0v11.25"
            />
          </svg>
          <span>View {subProjectDetails.type}</span>
        </span>
      </a>
    </div>
  </div>

  {#if subProjectDetails.pictures}
    <div class="container_image_screens desktop">
      {#each subProjectDetails.pictures as picture}
        <div class="bloc_image_screen">
          <img preload src="/assets/screens/{picture}.webp" alt={picture} />
        </div>
      {/each}
    </div>
  {/if}
  {#if subProjectDetails.picturesMobile}
    <div class="container_image_screens mobile">
      {#each subProjectDetails.picturesMobile as picture}
        <div class="bloc_image_screen">
          <img preload src="/assets/screens/{picture}.webp" alt={picture} />
        </div>
      {/each}
    </div>
  {/if}
  <ProjectsNavigation {nextProject} {prevProject} />
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

  @media (min-width: 1023px) {
    a::after {
      content: "";
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
    .svg_view_website {
      display: none;
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
