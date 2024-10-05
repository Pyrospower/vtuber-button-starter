<script lang="ts">
  export let category = "";
</script>

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

<style>
  h2 {
    font-size: 1.25rem;
    font-weight: 600;
    line-height: 1.75rem;
    margin-bottom: 0.875rem;
  }

  section {
    padding-block: 1rem;
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
