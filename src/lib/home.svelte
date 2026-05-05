<script>
  import { username } from "./library";
</script>

<div>
  <input
    type="text"
    id="name"
    bind:value={$username}
    placeholder="enter your name"
  />

  <p>hello {$username}</p>
</div>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Geom:ital,wght@0,300..900;1,300..900&display=swap");
  input {
    font-size: 40px;
    background-color: transparent;
    border: none;
    outline: none;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.3s ease;
    font-family: "Geom", sans-serif;
  }

  input:hover {
    border-bottom: 2px solid white;
  }
</style>
