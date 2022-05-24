<script>
  import SomeComponent from '$lib/SomeComponent.svelte';
  
  let something = false;
</script>

{#if something}
  <SomeComponent />
{/if}

<slot />