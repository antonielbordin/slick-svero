<script>
  import { onMount, beforeUpdate } from "svelte";
  import { isReloaded, currentRoute } from "./Router.svelte";
  
  onMount(console.log('sou o observer'));

  // capture url and refresh 
  beforeUpdate(checkRefresh);

  function checkRefresh() {
    console.log('capturar o refresh!');
    console.log('isReloaded: ' , $isReloaded);
    console.log('currentRoute: ', $currentRoute);
  }
</script>