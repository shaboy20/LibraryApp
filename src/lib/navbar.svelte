<script lang="ts">
  import Books from "./books.svelte";
  import Home from "./home.svelte";
  import Upload from "./upload.svelte";
  let page = "";
</script>

<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" />
<link
  href="https://fonts.googleapis.com/css2?family=Alice&family=Imperial+Script&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Source+Code+Pro:ital,wght@0,200..900;1,200..900&family=Tangerine:wght@400;700&display=swap"
  rel="stylesheet"
/>

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
  button {
    font-size: 40px;
    background-color: transparent;
    border: none;
    outline: none;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.3s ease;
    font-family: "Tangerine", cursive;
  }

  button:hover {
    border-bottom: 2px solid white;
  }
</style>
