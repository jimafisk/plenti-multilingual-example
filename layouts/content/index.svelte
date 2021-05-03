<script>
	export let title;
	import { onMount } from 'svelte/internal';

	onMount(() => window.location.replace("/pages/en"));
</script>

<h1>{title}</h1>

<style>
	:global(*) {
		font-family: Helvetica, sans-serif;
	}
</style>
