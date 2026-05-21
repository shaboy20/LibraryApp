<script>
  import { parsePhoneNumberWithError } from "libphonenumber-js";
  import { IsLoggedIn } from "$lib/userstate.svelte";
  import { userState } from "$lib/userstate.svelte";
  let phoneNumber = $state("");
  let password = $state("");
  let name = $state("");
  let errors = $state("");
  function bind() {
    try {
      let check = parsePhoneNumberWithError(phoneNumber);
      errors = "";
      if (password == "" || name == "" || password.length < 8) {
        throw new Error("Please put a valid password and name");
      }
      userState.phoneNumber = phoneNumber;
      userState.password = password;
      userState.name = name;
      IsLoggedIn.IsLoggedIn = true;
    } catch (error) {
      errors =
        "please enter a valid phone number , username and password where password should be over 8 charecters";
    }
  }
</script>

{#if IsLoggedIn.IsLoggedIn}
  <div>welcome back</div>
{:else}
  <div class="container">
    <input
      type="text"
      id="name"
      bind:value={name}
      placeholder="enter your name"
    />
    <input
      type="password"
      id="password"
      bind:value={password}
      placeholder="enter your password "
    />

    <input
      type="text"
      id="phoneNumber"
      bind:value={phoneNumber}
      placeholder="enter your phone number"
    />

    <div class="buttons">
      <button onclick={bind}>sign up</button>
      <button class="login" onclick={bind}>log in</button>
    </div>

    <p class="error">{errors}</p>
  </div>
{/if}

<style>
  @import url("https://fonts.googleapis.com/css2?family=Geom:ital,wght@0,300..900;1,300..900&display=swap");
  * {
    color: black;
  }

  :global(body) {
    background-image: url("/wallpaper.png");
    background-size: cover;
    background-repeat: no-repeat;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: calc(100vh - 100px);
    gap: 1.5rem;
  }

  .buttons {
    display: flex;
    gap: 1rem;
    margin-top: 1rem;
  }
  .error {
    color: red;
    margin-top: 1rem;
    text-align: center;
    font-family: "Geom", sans-serif;
  }
  button {
    font-family: "Geom", sans-serif;
    font-size: 1.5rem;
    padding: 0.5rem 1.5rem;
    background-color: transparent;
    border: 2px solid black;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  button:hover {
    background-color: black;
    color: white !important;
  }

  input {
    font-size: 40px;
    background-color: transparent;
    border: none;
    outline: none;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.3s ease;
    font-family: "Geom", sans-serif;
    text-align: center;
  }

  input:hover {
    border-bottom: 2px solid white;
  }
</style>
