<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<svelte:head>
	<title>SERAPHIC</title>
	<meta name="description" content="Chat app for enterprises" />
</svelte:head>

<main>
	{@render children()}
</main>
