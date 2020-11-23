<script context="module">
  import { writable } from "svelte/store";

  const routes = {};

  export const currentRoute = writable({});

  export const registerRoute = route => {
    routes[route.path] = route;
  };
</script>

<script>
  import page from "page";
  import { onMount, onDestroy } from "svelte";

  export let disabled = false;
  export let basePath = undefined;

  // this is where we set the active component
  const last = route => {
    return function(ctx) {
      $currentRoute = { ...route, params: ctx.params };
    };
  };

  const buildPage = () => {
    for (let [path, route] of Object.entries(routes)) {
      page(path, ...route.middleware, last(route));
    }
    // set the base url path for our router
    if (basePath) {
      page.base(basePath);
    }
    // setup page and its click handlers
    page.start();
  };

  // build the router when component is mounted
  onMount(buildPage);
  
  // remove click event handlers when component is unmounted
  onDestroy(page.stop);
</script>

<!-- don't render anything if component is disabled -->
{#if !disabled}
  <slot />
{/if}
