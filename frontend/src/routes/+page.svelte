<script>
	import Hero from '../components/Landing/Hero.svelte';
	import Navbar from '../components/Landing/Navbar.svelte';
</script>

<div class="h-screen w-screen bg-[url('/Background.jpg')] pt-4">
	<Hero />
	<Navbar />
</div>

<style>
	* {
		font-family: 'Courier New', Courier, monospace;
	}
</style>
