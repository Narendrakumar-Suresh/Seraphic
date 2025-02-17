<script lang="ts">
	import '../app.css';
	import Navbar from '../components/Landing/Navbar.svelte';
	let { children } = $props();
</script>

<svelte:head>
	<title>SERAPHIC</title>
	<meta name="description" content="Chat app for enterprises" />
</svelte:head>

<Navbar />
<main>
	{@render children()}
</main>
