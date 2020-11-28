<script>
  import { registerRoute, currentRoute } from "./Router.svelte";

  export let path = "/";
  export let component = null;
  export let middleware = [];

  let routeParams = {};

  registerRoute({ path, component, middleware });

  $: if ($currentRoute.path === path) {
    routeParams = $currentRoute.params;
  }
</script>
<!-- if this is current active route -->
{#if $currentRoute.path === path}
  <!-- prefer component over slot -->
  {#if $currentRoute.component}
    <svelte:component
      this={$currentRoute.component}
      {...$$restProps}
      {...routeParams} />
  {:else}
    <slot {routeParams} />
  {/if}
{/if}
