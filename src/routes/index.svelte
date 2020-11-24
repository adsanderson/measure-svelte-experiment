<script>
  import AdBlocker from "../components/AdBlocker.svelte";
  import { onMount } from "svelte";
  import Questions from "../components/Questions.svelte";

  //   if (gtag) {
  //     gtag("config", "G-YF9KGN3BL7", {
  //       custom_map: { metric1: "new_button" },
  //     });
  //   }

  let measureable = {
    state: false,
  };

  console.log(!!gtag);
  if (typeof window !== "undefined" && gtag) {
    console.log("set??");
    measureable.state = true;
  }

  function buttonHandler() {
    console.log("send event");

    gtag("event", "new_button_clicked", { new_button: "hi" });

    gtag("event", "button", {
      key: "test a button",
    });
  }
</script>

<style>
  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>

{#if !measureable.state}
  <AdBlocker />
{/if}

{#if measureable.state}
  <h1>Measure Experiment</h1>
  <p>
    Visit the
    <a href="https://svelte.dev/tutorial">Svelte tutorial</a>
    to learn how to build Svelte apps.
  </p>
  <button on:click={buttonHandler}>Click</button>
{/if}

<Questions />
