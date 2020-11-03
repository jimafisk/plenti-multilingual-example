<script>
  export let allContent, content;

  let lang = "en"; // set default language

  $: urlPrefix = content.path.split('/')[1] + "/";
  $: urlSuffix = content.filename == "index.json" ? "" : "/" + content.path.substring(content.path.lastIndexOf('/') + 1);
</script>

<nav>
  
  <span id="page-links">
  {#each allContent as page}
    {#if page.path.startsWith('/pages/'+lang) && page.filename == 'index.json'}
      <a href="{page.path}">Home</a>
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
    {#if page.path.startsWith('/pages/'+lang) && page.filename != 'index.json'}
      <a href="{page.path}">{page.fields.title}</a>
    {/if}
  {/each}
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
