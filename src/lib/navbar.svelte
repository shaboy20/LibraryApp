<script lang="ts">
  import Books from "./books.svelte";
  import Home from "./home.svelte";
  import Upload from "./upload.svelte";
  let page = "";
</script>

<div id="nav">
  <button id="HomePage" on:click={() => (page = "Home")}>Home Page</button>
  <button id="books" on:click={() => (page = "books")}>Books</button>
  <button id="UploadBook" on:click={() => (page = "UploadBook")}
    >Upload books</button
  >
</div>

{#if page === "Home"}
  <Home />
{:else if page === "books"}
  <Books />
{:else if page === "UploadBook"}
  <Upload />
{/if}

<style>
  @import url("https://fonts.googleapis.com/css2?family=Geom:ital,wght@0,300..900;1,300..900&display=swap");
  button {
    font-size: 40px;
    background-color: transparent;
    border: none;
    outline: none;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.3s ease;
    font-family: "Geom", cursive;
  }

  button:hover {
    border-bottom: 2px solid white;
  }
</style>
