<script>
  import { onMount } from "svelte";

  let progressValue = 0;

  onMount(() => {
    window.addEventListener("scroll", updateProgress);

    function updateProgress() {
      const totalHeight =
        document.documentElement.scrollHeight - window.innerHeight;
      const progress = (window.scrollY / totalHeight) * 100;
      progressValue = progress;
    }

    return () => {
      window.removeEventListener("scroll", updateProgress);
    };
  });
</script>

<progress id="progressBar" value={progressValue} max="100" />

<style>
  progress {
    width: 100%;
    position: fixed;
    height: 5px;
    appearance: none;
    background-color: transparent;
    border: none;
    color: #a1a1a1;
    z-index: 9999;
  }

  progress::-webkit-progress-bar {
    background-color: transparent;
  }

  progress::-moz-progress-bar {
    background-color: transparent;
  }

  progress::-ms-fill {
    background-color: transparent;
  }

  progress::-webkit-progress-value {
    background-color: #a1a1a1;
  }

  progress::-moz-progress-bar {
    background-color: #a1a1a1;
  }

  progress::-ms-fill {
    background-color: #a1a1a1;
  }
</style>
