<script lang="ts">
  let username: string = "";
  let password: string = "";
  let err: string = "";
  let msg: string = "";
  let showError: boolean = false;
  let success: boolean = false;
  const admin = {
    username: "admin",
    password: "password",
  };
  const login = async () => {
    if (username !== admin.username || password !== admin.password) {
      err = "Invalid credentials, please try again!";
      showError = true;
      await delay(3);
      err = "";
      showError = false;
      return;
    }

    msg = "Login successfully!";
    success = true;
    await delay(3);
    msg = "";
    success = false;
    username = "";
    password = "";
  };
  const delay = async (sec: number) => {
    return new Promise((resolve) => setTimeout(resolve, sec * 1000));
  };
</script>

<form on:submit|preventDefault={login}>
  <h1>Login</h1>
  <br />
  {#if showError}
    <p class="err">{err}</p>
  {/if}
  {#if success}
    <p class="success">{msg}</p>
  {/if}
  <p>Username</p>
  <input type="text" bind:value={username} />
  <br />
  <p>Password</p>
  <input type="password" bind:value={password} />
  <br />
  <br />
  <button type="submit"> Submit </button>
</form>

<style>
  .err {
    color: red;
  }
  .success {
    color: green;
  }
</style>
