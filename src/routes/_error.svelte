<script lang="ts">
  import { onMount } from 'svelte';
  import { goto } from '@sapper/app';

  onMount(() => {
    if (!dev && status === 404) {
      goto('/');
    }
  });

  export let status: number;
  export let error: Error;

  const dev = process.env.NODE_ENV === 'development';
</script>

<svelte:head>
  <title>{status}</title>
</svelte:head>

<h1>{status}</h1>

<p>{error.message}</p>

{#if dev && error.stack}
  <pre>{error.stack}</pre>
{/if}
