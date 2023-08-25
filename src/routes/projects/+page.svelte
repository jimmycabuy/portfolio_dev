<script>
  import projectsJSON from "../../data/projects.json";
  import { blur } from "svelte/transition";

  let currentProject = null;

  const setProject = (e) => {
    currentProject = e;
  };
</script>

<svelte:head>
  <title>Jimmy C. | My Work..</title>
</svelte:head>

<main class="px-12 flex justify-center items-center 4xl:px-72" in:blur>
  <div class="container_projects">
    <div class="bloc_left">
      {#each projectsJSON as project}
        <!-- svelte-ignore a11y-mouse-events-have-key-events -->
        <a
          href="projects/{project.route}"
          on:mouseover={() => setProject(project)}
          on:mouseout={() => setProject(null)}
        >
          <div class="one_project">
            <div class="flex items-center">
              <span
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="w-6 h-6"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75"
                  />
                </svg>
              </span>
              <div class="title-wrapper">
                <h2 class="text-sm sm:text-lg">{project.title}</h2>
                <p class="tag text-xs sm:text-xs">{project.tag}</p>
              </div>
            </div>
            <h4 class="text-xs sm:text-lg">{project.subtitle}</h4>
          </div>
        </a>
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

  .one_project {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 5rem;
    position: relative;
  }

  a {
    border-bottom: 2px solid #a1a1a1;
  }

  .bloc_left a:last-child {
    border:none;
  }

  .tag {
    border: 1px solid #fff;
    border-radius: 20px;
    padding: 2px 7px;
    color: #fff;
    padding-top: 3px;
  }

  h4 {
    color: #a1a1a1;
  }

  svg {
    fill: #fff;
    margin-bottom: 3px;
    padding-right: 5px;
  }

  .one_project span {
    display: none;
  }

  @media (min-width: 1023px) {
    .one_project .title-wrapper {
      transition: transform 0.3s ease;
    }

    .one_project:hover .title-wrapper {
      transform: translateX(20px);
    }

    .one_project span {
      display: block;
      position: absolute;
      left: -20px; /* Ajustez la position de départ */
      opacity: 0;
      transition: left 0.3s ease, opacity 0.3s ease;
    }

    .one_project:hover span {
      left: 0; /* Ajustez la position d'arrivée */
      opacity: 1;
    }
  }

  .title-wrapper {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  /* .one_project:hover .title-wrapper {
    animation: bounce 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55) alternate;
  }

  @keyframes bounce {
    from {
      transform: translateX(0);
    }
    to {
      transform: translateX(20px);
    }
  } */

  p {
    color: #a1a1a1;
  }

  @media (max-width: 387px) {
    .tag {
      display: none;
    }
  }

  @media (max-width: 1023px) {
    .bloc_right {
      display: none;
    }
    .bloc_left {
      width: 100%;
      padding: 0;
    }
  }
</style>
