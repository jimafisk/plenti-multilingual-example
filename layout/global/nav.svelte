<script>
  export let allContent, content;

  let lang = "en"; // set default language
  const setLang = selectedLang => {
    lang = selectedLang;
  }

  $: urlPrefix = content.path.split('/')[1] + "/";
  $: urlSuffix = "/" + content.path.substring(content.path.lastIndexOf('/') + 1);
</script>

<nav>
  
  <a href="/">Home</a>

  <span id="lang-switcher">
    <strong>language:</strong>
    <a href="/{urlPrefix}en{urlSuffix}" on:click={() => setLang("en")}>en</a>
    <a href="/{urlPrefix}fr{urlSuffix}" on:click={() => setLang("fr")}>fr</a>
  </span>

  <span id="page-links">
  {#each allContent as page}
    {#if page.path.startsWith('/pages/'+lang)}
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
