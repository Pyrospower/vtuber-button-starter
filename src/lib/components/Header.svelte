<script lang="ts">
  import { toggleMode } from "mode-watcher";
</script>

<div class="btn-wrapper">
  <button class="mode-toggle" on:click={toggleMode}>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="sun"
      ><circle cx="12" cy="12" r="4" /><path d="M12 2v2" /><path
        d="M12 20v2"
      /><path d="m4.93 4.93 1.41 1.41" /><path
        d="m17.66 17.66 1.41 1.41"
      /><path d="M2 12h2" /><path d="M20 12h2" /><path
        d="m6.34 17.66-1.41 1.41"
      /><path d="m19.07 4.93-1.41 1.41" /></svg
    >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="moon"><path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z" /></svg
    >
    <span class="sr-only">Toggle Mode</span>
  </button>
</div>

<style>
  .btn-wrapper {
    display: flex;
    align-items: center;
    position: fixed;
    top: 1rem;
    right: 1rem;
    z-index: 20;
  }

  .mode-toggle {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    white-space: nowrap;
    border: none;
    border-radius: calc(var(--radius) - 2px);
    font-size: 0.875rem;
    line-height: 1.25rem;
    transition-property: color, background-color, border-color,
      text-decoration-color, fill, stroke;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 0.15s;
    padding-block: 0.5rem;
    height: 2rem;
    width: 2rem;
    padding-inline: 0;

    &:hover {
      background-color: hsl(var(--clr-accent));
      color: hsl(var(--clr-accent-foreground));
    }

    &:focus-visible {
      outline-offset: 2px;
    }
  }

  .moon,
  .sun {
    position: absolute;
    height: 1.2rem;
    width: 1.2rem;
    transition: all cubic-bezier(0.4, 0, 0.2, 1) 0.15s;
  }

  .sun {
    rotate: 0deg;
    scale: 1;
  }

  :global(.dark) .sun {
    rotate: -90deg;
    scale: 0;
  }

  .moon {
    rotate: 90deg;
    scale: 0;
  }

  :global(.dark) .moon {
    rotate: 0deg;
    scale: 1;
  }

  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
  }
</style>
