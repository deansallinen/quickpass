<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";
  import generatePassword from "password-generator";
  import confetti from "canvas-confetti";
  let pwd;
  onMount(() => {
    confetti.create(document.getElementById("canvas"), {
      resize: true,
      useWorker: true
    })({ particleCount: 200, spread: 200, origin: { y: 0.45 } });
    pwd = generatePassword(20);
  });
</script>

<style>
  main {
    display: flex;
    height: 100vh;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    max-width: 240px;
    margin: 0 auto;
  }

  h2 {
    font-size: 5vw;
    font-weight: bold;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<svelte:head>
  <title>PWD</title>
</svelte:head>

<main>
  {#if pwd}
    <h2 transition:fade={{ duration: 200 }}>{pwd}</h2>
  {/if}
</main>
