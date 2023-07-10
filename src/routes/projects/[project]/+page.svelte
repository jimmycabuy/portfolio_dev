<script>
  import { page } from "$app/stores";
  const project = $page.params.project;
  import projectsJSON from "../../../data/projects.json";
  const subProjectDetails = projectsJSON.find((item) => item.route === project);
</script>

<main
  class="py-6 px-12 flex-1 flex justify-center items-center flex-col md:px-24"
>
  <div class="container_image flex justify-center">
    <div class="bloc_image">
      <img
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
            class="w-5 h-5"
            color="#fff"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4.5 19.5l15-15m0 0H8.25m11.25 0v11.25"
            />
          </svg>
          <span>View website</span>
        </span>
      </a>
    </div>
  </div>
</main>

<style>
  main {
    z-index: 1;
  }

  h1 {
    margin-bottom: 2rem;
    font-size: xx-large;
    border-bottom: 2px solid #fff;
    text-transform: uppercase;
  }

  .container_image {
    width: 75%;
    margin-top: -7rem;
  }
  .bloc_image {
    border-radius: 0 0 40px 40px;
    overflow: hidden; /* Pour cacher les parties de l'image dépassant du bloc */
    margin-bottom: 2rem;
  }

  .bloc_image img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Pour ajuster l'image en conservant son ratio d'aspect */
  }

  .container_one_project {
    display: flex;
    flex-direction: row;
    height: 100%;
    width: 75%;
    gap: 1rem;
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
    width: 30%;
    text-align: left;
  }

  .col2 {
    width: 70%;
    text-align: left;
  }

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

  .view_website {
    width: fit-content;
    max-width: fit-content;
    display: inline-flex;
  }

  @media (max-width: 1023px) {
    .container_one_project {
      flex-direction: column;
      font-size: smaller;
    }

    .bloc_title,
    .container_image,
    .container_one_project {
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
    svg {
      display: none;
    }
    a {
      color: #a1a1a1;
    }
  }
</style>
