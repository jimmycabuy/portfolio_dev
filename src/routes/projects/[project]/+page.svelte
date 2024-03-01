<script>
  import ProjectPage from "../../../components/ProjectPage.svelte";
  import Spinner from "../../../components/Spinner.svelte";

  let isLoading = true;

  setTimeout(() => {
    isLoading = false;
  }, 1250);
</script>

{#if isLoading}
  <Spinner />
{/if}

<ProjectPage {isLoading} />
