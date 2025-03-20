<script>
  import { createEventDispatcher } from 'svelte';

  export let project;

  const dispatch = createEventDispatcher();

  const setProject = (e) => {
    dispatch('project', e);
  };
</script>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
{#if project.displayProject}
  <a
    class="enlarged link"
    href="/projects/{project.route}"
    on:mouseover={() => setProject(project)}
    on:mouseout={() => setProject(null)}
  >
    <div class="enlarged one_project">
      <div class="enlarged flex items-center w-full sm:w-fit">
        <span
          ><svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="enlarged w-6 h-6"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
          </svg>
        </span>
        <div class="enlarged title-wrapper justify-between w-full">
          <h2 class="enlarged sm:text-lg">{project.title}</h2>
          <p class="enlarged tag text-xs sm:text-xs">{project.tag}</p>
        </div>
      </div>
      <h4 class="enlarged text-right hidden sm:text-lg sm:contents">
        {project.subtitle}
      </h4>
    </div>
  </a>
{/if}

<style>
  .one_project {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 5rem;
    position: relative;
  }

  a {
    border-bottom: 2px solid #fff;
  }

  a:last-child {
    border: none;
  }

  .tag {
    border: 1px solid #fff;
    border-radius: 20px;
    padding: 2px 7px;
    color: #fff;
    padding-bottom: 3px;
  }

  h4 {
    color: #fff;
  }

  svg {
    fill: #fff;
    margin-bottom: 3px;
    padding-right: 5px;
  }

  .one_project span {
    display: none;
  }

  @media (min-width: 1023px) and (pointer: fine) {
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
      transition:
        left 0.3s ease,
        opacity 0.3s ease;
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

  p {
    color: #fff;
  }

  @media (max-width: 387px) {
    .tag {
      display: none;
    }
  }
</style>
