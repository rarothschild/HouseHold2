<script lang="ts">
  import { currentUser } from './lib/pocketbase'
  import SplashPage from "./lib/SplashPage.svelte";
  import Residences from './lib/Residences.svelte';
  import Header from "./lib/Header.svelte";
  
</script>

<main class="h-screen bg-sky-400">
  <Header />
  <h1 class=" bg-slate-400">Welcome to Household</h1>
  {#if $currentUser}
    <SplashPage />
  {:else}
    <Residences />
  {/if}
</main>

