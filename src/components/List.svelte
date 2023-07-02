<script>
  export let project;
</script>

<li>
  <img
    src={`/assets/${project.li_file}.png`}
    title={project.li_title}
    alt={project.li_alt}
  />
</li>

<style>
  img {
    height: 35px;
    width: 35px;
  }
</style>
