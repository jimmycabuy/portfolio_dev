<main class="px-10 xl:px-36 py-6 mt-10 w-full">
  <h1 class="my-10 text-5xl md:text-7xl">Timeline</h1>
  <div class="grid_container">
    <div class="div1">
      <h2>2015-2016</h2>
      <h2>Australia</h2>
    </div>
    <div class="div2">
      <h2>2016-2019</h2>
      <h2>E-bussines student</h2>
    </div>
    <div class="div3">
      <h2>2018-2021</h2>
      <h2>Digital Marketing Expert</h2>
    </div>
    <div class="div4">
      <h2>2019-2024</h2>
      <h2>Photographer</h2>
    </div>
    <div class="div5">
      <h2>2022-2024</h2>
      <h2>Web Developer</h2>
    </div>
  </div>
</main>

<style>
  @media (min-width: 1023px) {
    .grid_container {
      display: grid;
      grid-template-columns: repeat(9, 1fr);
      grid-template-rows: repeat(5, 1fr);
      grid-row-gap: 1.5rem;
      width: 100%;
    }

    .div1 {
      grid-area: 1 / 1 / 2 / 2;
      border: 2px solid #fff;
      border-radius: 3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 5rem;
      flex-direction: column;
    }
    .div2 {
      grid-area: 2 / 2 / 3 / 5;
      border: 2px solid #fff;
      border-radius: 3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 5rem;
      flex-direction: column;
    }
    .div3 {
      grid-area: 3 / 4 / 4 / 7;
      border: 2px solid #fff;
      border-radius: 3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 5rem;
      flex-direction: column;
    }
    .div4 {
      grid-area: 4 / 5 / 5 / 10;
      border: 2px solid #fff;
      border-radius: 3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 5rem;
      flex-direction: column;
    }
    .div5 {
      grid-area: 5 / 8 / 6 / 10;
      border: 2px solid #fff;
      border-radius: 3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 5rem;
      flex-direction: column;
    }
  }

  @media (max-width: 1022px) {
    .grid_container {
      width: 100%;
      display: flex;
      gap: 1.5rem;
      flex-direction: column;
    }

    .div1,
    .div2,
    .div3,
    .div4,
    .div5 {
      border: 2px solid #fff;
      border-radius: 3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 5rem;
      flex-direction: column;
    }
  }

  h1{
    color: transparent;
    -webkit-text-stroke: 2px #fff;
    font-weight: 700;
  }
</style>
