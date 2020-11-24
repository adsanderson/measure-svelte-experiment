<script>
  export let name;

  gtag("config", "G-YF9KGN3BL7", {
    custom_map: { metric1: "new_button" },
  });

  function buttonHandler() {
    console.log("send event");

    gtag("event", "new_button_clicked", { new_button: "hi" });

    gtag("event", "button", {
      key: "test a button",
    });
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the
    <a href="https://svelte.dev/tutorial">Svelte tutorial</a>
    to learn how to build Svelte apps.
  </p>
  <button on:click={buttonHandler}>Click</button>
</main>
