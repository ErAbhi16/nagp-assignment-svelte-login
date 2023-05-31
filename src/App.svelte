<script lang="ts">
  import { onMount } from 'svelte';
  import Dashboard from './lib/Dashboard.svelte';
  import LoginForm from './lib/LoginForm.svelte';

  let loggedIn = false;
  let username = '';

  function handleLoginSuccess(event) {
    loggedIn = true;
    username = event.detail.username;
  }
</script>

<main>
  {#if loggedIn}
    <Dashboard {username} />
  {:else}
    <div>
      <h1>Login</h1>
      <LoginForm on:success={handleLoginSuccess} />
    </div>
  {/if}
</main>

<style>
  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  div {
    max-width: 300px;
    margin: 0 auto;
    padding: 40px;
  }

  h1 {
    text-align: center;
  }
</style>
