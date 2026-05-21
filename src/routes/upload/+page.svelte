<script>
  import { IsLoggedIn } from "$lib/userstate.svelte";
  //title
  //author
  //cover page
  //first page of the book
  //back page of the book
</script>

{#if IsLoggedIn.IsLoggedIn}
  <textarea name="title" id="title" placeholder="Enter the book title"
  ></textarea>
  <textarea name="author" id="author" placeholder="Enter the author"></textarea>
  <textarea
    name="summary"
    id="summary"
    placeholder="Enter a summary of the book"
  ></textarea>
  <input name="coverpage" type="file" />
  <button>Submit</button>
{:else}
  <a href="/" style="text-decoration: none;">Please log in or sign up</a>
{/if}

<style>
  :global(body) {
    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 20px;
    background-image: url("/wallpaper.png");
  }

  textarea,
  input {
    max-width: 200px;
    position: relative;
    left: 40vw;
    background-color: transparent;
    backdrop-filter: blur(5px);
    border: solid 2px black;
    border-radius: 4px;
    outline: none;
  }

  button {
    position: relative;
    left: 45vw;
    width: 100px;
    background-color: transparent;
    backdrop-filter: blur(5px);
    outline: none;
    border: 2px solid black;
    border-radius: 4px;
  }

  #summary {
    height: 200px;
  }

  input {
    background-color: transparent !important;
    max-width: 100px;
    position: relative;
    left: 45vw;
  }

  * {
    color: black;
  }
</style>
