<script>
  import { page } from '$app/stores';
</script>

<main>
  <h1>{$page.status}</h1>
  <h1>Oops! Page not found</h1>
  <h4>Sorry, the page you are looking for does not exist.</h4>
  <a href="/" class="enlarged">Homepage</a>
</main>

<style>
  main {
    height: 70vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 1;
  }
  a {
    margin-top: 1rem;
  }

  a {
    position: relative;
    text-decoration: none;
    color: #fff;
    width: fit-content;
  }

  @media (min-width: 1023px) {
    main {
      height: 80vh;
    }
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
</style>
