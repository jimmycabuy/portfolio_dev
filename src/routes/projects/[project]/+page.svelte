<script>
  import { page } from "$app/stores";
  import projectsJSON from "../../../data/projects.json";
  import ProjectPage from "../../../components/ProjectPage.svelte";
  import ProgressBar from "../../../components/ProgressBar.svelte";
  import Spinner from "../../../components/Spinner.svelte";
  import { onMount } from "svelte";
  import { gsap } from "gsap";

  let isLoading = true;

  onMount(() => {
    gsap.from(".container_image", {
      y: -500,
      duration: 1,
      delay: 1.35,
      opacity: 0,
    });

    gsap.from(".bloc_title, .container_one_project, .container_image_screens", {
      duration: 3,
      delay: 2.35,
      opacity: 0,
    });
  });

  setTimeout(() => {
    isLoading = false;
  }, 1250);

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
  <title>Jimmy C. | {subProjectDetails.title}.</title>
</svelte:head>

{#if isLoading}
  <Spinner />
{/if}

<ProgressBar />
<ProjectPage {isLoading} {nextProject} {prevProject} {subProjectDetails} />
