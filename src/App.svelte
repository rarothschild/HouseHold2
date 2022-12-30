<script lang="ts">
  import { currentUser } from './lib/pocketbase'
  import Login from './lib/Login.svelte';
  import Residences from './lib/Residences.svelte';
</script>

<main>
  <h1>Welcome to Household</h1>
  {#if $currentUser}
    <Residences />
  {:else}
    <Login />
  {/if}
  
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>