<script>
  import { page } from "$app/stores";
  import projects from "../../../data/projects.json";
  import ProjectPage from "../../../components/ProjectPage.svelte";
  import Spinner from "../../../components/Spinner.svelte";

  let isLoading = true;

  setTimeout(() => {
    isLoading = false;
  }, 1250);

  const project = $page.params.project;
  const currentProjectIndex = projects.findIndex(
    (item) => item.route === project
  );
  const totalProjects = projects.length;
  const nextIndex = (currentProjectIndex + 1) % totalProjects;
  const prevIndex = (currentProjectIndex - 1 + totalProjects) % totalProjects;
  const currentProjectDetails = projects[currentProjectIndex];
  const nextProjectDetails = projects[nextIndex];
  const prevProjectDetails = projects[prevIndex];
</script>

<svelte:head>
  <title>Jimmy C. | {currentProjectDetails.title}.</title>
</svelte:head>

{#if isLoading}
  <Spinner />
{/if}

<ProjectPage
  {isLoading}
  {nextProjectDetails}
  {prevProjectDetails}
  {currentProjectDetails}
/>
