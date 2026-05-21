<script lang="ts">
  let { children } = $props();
  import { IsLoggedIn } from "$lib/userstate.svelte";
</script>

<nav>
  {#if IsLoggedIn.IsLoggedIn}
    <a href="/">home</a>
    <a href="/books">books</a>
    <a href="/upload">upload books</a>
  {:else}
    <a href="/">Login/Sign up</a>
  {/if}
</nav>

{@render children()}

<style>
  @import url("https://fonts.googleapis.com/css2?family=Geom:ital,wght@0,300..900;1,300..900&display=swap");
  * {
    text-decoration: none;
  }

  nav {
    height: 20px;
    border-bottom: medium solid black;
    display: flex;
    flex-direction: row;
    gap: 20px;
    padding-bottom: 20px;
  }

  a {
    color: black;
  }

  :global(body) {
    background-image: url("/wallpaper.png");
  }
</style>
