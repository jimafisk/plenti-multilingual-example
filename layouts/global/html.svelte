<script>
  import Head from './head.svelte';
  import Nav from './nav.svelte';

  export let layout, content, allContent, user, admin;
</script>

<html lang="en">
<Head title={content.filename} />
<body>
  {#if user && $user.isAuthenticated}
    <svelte:component this={$user.menu} bind:content {user} />
  {/if}
  <main>
    <Nav {allContent} {content} {user} />
    <svelte:component this={layout} {...content.fields} {allContent} />
  </main>
</body>
</html>
