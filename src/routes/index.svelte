<script context="module" lang="ts">
  import { rankServiceImpl } from '../service';

  export async function preload() {
    await rankServiceImpl.getRank();
  }
</script>

<script lang="ts">
  import {
    Header,
    Navigation,
    Information,
    Register,
    Spinner,
    Rank,
  } from '../views';

  import { modal, loading } from '../data';

  let currentModal = modal.getStore();
</script>

<style lang="scss">
  @import '../utils/styles/theme.scss';

  :global(*) {
    font-family: 'Noto Sans KR', sans-serif;
    box-sizing: border-box;
  }

  :global(html) {
    font-size: 14px;

    @media (max-width: $mobile-width) {
      font-size: 12px;
    }
  }

  :global(body) {
    margin: 0;
    padding: 0;
  }

  :global(img) {
    user-select: none;
    -moz-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
    -ms-user-select: none;
  }

  :global(.layout) {
    margin: 0 auto;
    width: 70%;

    @media (max-width: 1400px) {
      width: 95%;
    }
  }

  :global(.flex) {
    display: flex;
  }

  :global(.flex-column) {
    flex-direction: column;
  }

  :global(.justify-center) {
    justify-content: center;
  }

  :global(.justify-space_between) {
    justify-content: space-between;
  }

  :global(.align-center) {
    align-items: center;
  }

  :global(.cursor-pointer) {
    cursor: pointer;
  }

  :global(code) {
    background-color: #272822;
    color: #f8f8f2;
    border-radius: 0.3rem;
    padding: 0.25rem;
  }
</style>

<svelte:head>
  <title>DSMGR</title>
</svelte:head>

<Header />

<div class="layout">
  <Navigation />
  <Rank />
</div>

{#if $currentModal === 'information'}
  <Information />
{:else if $currentModal === 'register'}
  <Register />
{/if}

{#if $loading}
  <Spinner />
{/if}
