<script>
  import { registerRoute, currentRoute } from "./Router.svelte";

  // page.js catch all handler
  export let path = "*";
  export let component = null;

  // need to set empty middlware. Otherwise we get an error
  registerRoute({ path, component, middleware: [] });
</script>
<svelte:options tag="svero-notfound" />
{#if $currentRoute.path === path}
  <svelte:component this={component} />
  <slot />
{/if}