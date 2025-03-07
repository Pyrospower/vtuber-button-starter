<script lang="ts">
  import CategorySection from "$lib/components/CategorySection.svelte";
  import Footer from "$lib/components/Footer.svelte";
  import ModeToggle from "$lib/components/ModeToggle.svelte";
  import { ModeWatcher } from "mode-watcher";
  import { SITE } from "./site-config";

  import voices from "./assets/voices.json";

  const { categories } = voices;
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

<ModeWatcher />
<div class="box">
  <ModeToggle />
  <main>
    <h1>{SITE.title}</h1>
    {#each categories as category}
      <CategorySection {category} />
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

    --clr-accent: 240 4.8% 95.9%;
    --clr-accent-foreground: 240 5.9% 10%;
    --clr-background: 0 0% 100%;
    --clr-foreground: 240 10% 3.9%;
    --clr-muted: 240 4.8% 95.9%;
    --clr-muted-foreground: 240 3.8% 46.1%;
    --clr-primary: 240 5.9% 10%;
    --clr-primary-foreground: 0 0% 98%;
    --radius: 0.5rem;

    accent-color: hsl(var(--clr-primary));
  }

  :global(.dark) {
    --clr-accent: 240 3.7% 15.9%;
    --clr-accent-foreground: 0 0% 98%;
    --clr-background: 240 10% 3.9%;
    --clr-foreground: 0 0% 98%;
    --clr-muted: 240 3.7% 15.9%;
    --clr-muted-foreground: 240 5% 64.9%;
    --clr-primary: 0 0% 98%;
    --clr-primary-foreground: 240 5.9% 10%;
  }

  :global(button, [role="button"]) {
    cursor: pointer;
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
    @media screen and (min-width: 768px) {
      padding: 2rem;
    }
  }

  h1 {
    font-size: 1.5rem;
    line-height: 2rem;
    font-weight: 700;
    margin-bottom: 1rem;
  }
</style>
