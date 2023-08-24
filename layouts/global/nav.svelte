<script>
  export let allContent, content, user;

  let lang = content.path.split('/')[1]; // set default language

  $: urlPrefix = content.path.split('/')[0] + "/";
  $: urlSuffix = content.filename == "_index.json" ? "" : "/" + content.path.substring(content.path.lastIndexOf('/') + 1);
</script>

<nav>
  
  <span id="page-links">
  {#each allContent as page}
    {#if page.path.startsWith('pages/'+lang) && page.filename == '_index.json'}
      <a href="/{page.path}">{lang == 'en' ? 'Home' : 'Maison'}</a>
    {/if}
  {/each}
  </span>

  <span id="lang-switcher">
    <strong>language:</strong>
    <a href="/{urlPrefix}en{urlSuffix}" on:click={() => lang = "en"}>en</a>
    <a href="/{urlPrefix}fr{urlSuffix}" on:click={() => lang = "fr"}>fr</a>
  </span>

  <span id="page-links">
  {#each allContent as page}
    {#if page.path.startsWith('pages/'+lang) && page.filename != '_index.json'}
      <a href="/{page.path}">{page.fields.title}</a>
    {/if}
  {/each}
  {#if user && $user.isAuthenticated}
    <button on:click|preventDefault={$user.logout()}>{lang == 'en' ? 'Logout' : 'Se déconnecter'}</button>
  {:else}
    <button on:click|preventDefault={$user.login()}>{lang == 'en' ? 'Login' : 'Se connecter'}</button>
  {/if}
  </span>

  <span id="auth">
  </span>

</nav>

<style>
  nav {
    display: flex;
    justify-content: space-between;
  }
  #page-links a {
    margin-right: 10px;
  }
</style>
