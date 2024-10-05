<script lang="ts">
  import Footer from "$lib/components/Footer.svelte";
  import Header from "$lib/components/Header.svelte";
  import { SITE } from "./site-config";

  let categories = ["Greeting", "General", "Catchphrases", "Laughing", "Cute"];
</script>

<svelte:head>
  <meta name="description" content={SITE.description} />
  <meta
    name="keywords"
    content="vtuber, virtual, youtuber, soundboard, noises"
  />
  <meta property="og:site_name" content={SITE.title} />
  <meta property="og:type" content="website" />
  <meta property="og:title" content={SITE.title} />
  <meta property="og:description" content={SITE.description} />
</svelte:head>

<div class="box">
  <Header />
  <main>
    <h1>{SITE.title}</h1>
    {#each categories as category}
      <section>
        <h2>{category}</h2>
        <div>
          {#each Array(5) as _, i}
            <button on:click={() => console.log("Playing sound")}>
              {category}
              {i + 1}
            </button>
          {/each}
        </div>
      </section>
    {/each}
  </main>
  <Footer />
</div>

<style>
  :global(:root) {
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;

    font-synthesis: none;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    --clr-background: 0 0% 100%;
    --clr-foreground: 240 10% 3.9%;
    --clr-muted: 240 4.8% 95.9%;
    --clr-muted-foreground: 240 3.8% 46.1%;
    --clr-primary: 240 5.9% 10%;
    --clr-primary-foreground: 0 0% 98%;
  }

  .box {
    display: flex;
    flex-direction: column;
    min-height: 100svh;
    position: relative;
  }

  main {
    flex-grow: 1;
    padding: 1rem;
    background-color: hsl(var(--clr-background));
    color: hsl(var(--clr-foreground));
    &:not(:last-child) {
      margin-bottom: 2rem;
    }
  }

  h2 {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
  }

  section > div {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }

  button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    width: fit-content;
    white-space: nowrap;
    border-radius: calc(0.5rem - 2px);
    border-width: 0;
    padding-inline: 1rem;
    padding-block: 0.5rem;
    font-size: 0.875rem;
    line-height: 1.25rem;
    font-weight: 500;
    transition-property: color, background-color, border-color, fill, stroke;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
    background-color: hsl(var(--clr-primary));
    color: hsl(var(--clr-primary-foreground));
    &:hover {
      background-color: hsl(var(--clr-primary) / 90%);
    }
    &:focus-visible {
      outline: 2px solid hsl(var(--clr-primary));
      outline-offset: 2px;
    }
  }
</style>
