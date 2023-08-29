<main />

<style>
  main {
    position: fixed;
    z-index: -10;
    top: -300%;
    left: -150%;
    height: 600%;
    width: 600%;
    -webkit-animation: bg-animation 7s steps(10) infinite;
    animation: bg-animation 7s steps(10) infinite;
    background-image: url("https://itssharl.ee/noise.png");
    background-size: 200px;
    background-repeat: repeat;
    opacity: 0.12;
    pointer-events: none;
  }

  @keyframes bg-animation {
    0% {
      transform: translate(0, 0);
    }
    10% {
      transform: translate(-5%, -5%);
    }
    20% {
      transform: translate(-10%, 5%);
    }
    30% {
      transform: translate(5%, -10%);
    }
    40% {
      transform: translate(-5%, 15%);
    }
    50% {
      transform: translate(-10%, 5%);
    }
    60% {
      transform: translate(15%, 0);
    }
    70% {
      transform: translate(0, 10%);
    }
    80% {
      transform: translate(-15%, 0);
    }
    90% {
      transform: translate(10%, 5%);
    }
    100% {
      transform: translate(5%, 0);
    }
  }
</style>
