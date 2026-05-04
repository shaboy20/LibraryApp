<div>Home placeholder :D</div>
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
  input {
    font-size: 40px;
    background-color: transparent;
    border: none;
    outline: none;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.3s ease;
    font-family: "Tangerine", cursive;
  }

  input:hover {
    border-bottom: 2px solid white;
  }
</style>
