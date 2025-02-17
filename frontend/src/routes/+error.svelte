<script lang="ts">
	import { page } from '$app/state';
</script>

<div class="flex h-screen w-screen flex-col items-center justify-center text-center">
	{#if page.error}
		<h1 class="text-2xl sm:text-4xl md:text-5xl lg:text-7xl">
			{page.status}
			{page.error.message}
		</h1>
	{:else}
		<h1 class="text-2xl sm:text-4xl md:text-5xl lg:text-7xl">An unknown error occurred</h1>
	{/if}
	<a href="/" class="mt-4 text-xl hover:underline">Go back to Home</a>
</div>
