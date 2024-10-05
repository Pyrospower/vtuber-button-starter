<script lang="ts">
  import { SITE, SOCIAL } from "../../site-config";
</script>

<footer>
  <p>
    &copy; {new Date().getFullYear()}
    {SITE.title}. All rights reserved.
  </p>
  <p>
    This is a fan-made project and is not affiliated with any official entities
    or VTubers.
  </p>
  <p>
    For more information and to contribute, visit our
    <a href={SOCIAL.github} target="_blank">GitHub Page.</a>
  </p>
</footer>

<style>
  footer {
    padding: 1rem;
    background-color: hsl(var(--clr-muted));
    color: hsl(var(--clr-muted-foreground));
    font-size: 0.875rem;
  }

  a {
    color: hsl(210 100% 50%);
    transition: opacity 0.2s ease;
    &:hover {
      opacity: 0.8;
    }
  }
</style>
