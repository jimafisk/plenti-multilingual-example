<script>
  import Head from './head.svelte';
  import Nav from './nav.svelte';

  export let route, content, allContent;
</script>

<html lang="en">
<Head title={content.filename} />
<body>
  <Nav {allContent} {content} />
  <svelte:component this={route} {...content.fields} {allContent} />
</body>
</html>
