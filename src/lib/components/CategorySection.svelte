<script lang="ts">
  interface Props {
    category: {
      name: string;
      voiceList: { name: string; path: string }[];
    };
  }

  let { category }: Props = $props();

  const playSound = (path: string) => () => {
    const audio = new Audio(path);
    audio
      .play()
      .catch((e) => console.error(`Failed to play audio: ${path}`, e));
  };
</script>

<section>
  <h2>{category.name}</h2>
  <div>
    {#each category.voiceList as voice}
      <button
        aria-label={`Play ${voice.name}`}
        onclick={playSound(`/voices/${category.name}/${voice.path}`)}
      >
        {voice.name}
      </button>
    {/each}
  </div>
</section>

<style>
  h2 {
    font-size: 1.25rem;
    font-weight: 600;
    line-height: 1.75rem;
    margin-bottom: 0.875rem;
  }

  section {
    background-color: hsl(var(--clr-muted));
    border-radius: 1.5rem;
    padding: 1rem;
    &:not(:last-child) {
      margin-block: 1rem;
    }
    & > div {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
    }
  }

  button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: fit-content;
    white-space: nowrap;
    border-radius: calc(var(--radius) - 2px);
    border-width: 0;
    padding-inline: 1rem;
    padding-block: 0.5rem;
    font-size: 0.875rem;
    line-height: 1.25rem;
    font-weight: 600;
    transition-property: color, background-color, border-color, fill, stroke;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
    -webkit-box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
    background-color: hsl(var(--clr-primary));
    color: hsl(var(--clr-primary-foreground));

    &:hover {
      background-color: hsl(var(--clr-primary) / 90%);
    }
    &:focus-visible {
      outline-offset: 2px;
    }
  }
</style>
