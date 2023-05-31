<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  let username = '';
  let password = '';
  let error = '';

  const dispatch = createEventDispatcher();

  async function handleLogin() {
    // Simulate async login request
    try {
        if (username === 'admin' && password === 'password') {
        dispatch('success', { username });
      } else {
        error = 'Invalid username or password';
      }
    } catch (error) {
      error = 'An error occurred during login';
    }
  }
</script>

<main>
  {#if error}
    <p>{error}</p>
  {/if}

  <form on:submit|preventDefault={handleLogin}>
    <label>
      Username:
      <input type="text" bind:value={username} />
    </label>

    <label>
      Password:
      <input type="password" bind:value={password} />
    </label>

    <button type="submit">Login</button>
  </form>
</main>

<style>
  main {
    max-width: 300px;
    margin: 0 auto;
    padding: 40px;
  }

  p {
    color: red;
    margin-bottom: 10px;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 20px;
  }

  label {
    display: flex;
    flex-direction: column;
  }

  input {
    padding: 5px;
  }

  button {
    padding: 10px;
  }
</style>
