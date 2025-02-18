<script>
	import { GithubLogo } from 'phosphor-svelte';
	import { fly } from 'svelte/transition';
	let isOpen = false;

	// Navigation items
	const navItems = [
		{ href: '/download', label: 'Download' },
		{ href: '/blogs', label: 'Blogs' }
	];

	// Toggle mobile menu
	function toggleMenu() {
		isOpen = !isOpen;
	}
</script>

<header class="fixed top-0 z-50 w-full bg-transparent shadow-sm">
	<nav class="container mx-auto px-12 text-white sm:px-6 lg:px-8">
		<div class="flex h-16 items-center justify-between">
			<a href="/" class="text-2xl font-bold"> SERAPHIC </a>

			<div class="hidden items-center justify-between space-x-8 md:flex">
				{#each navItems as { href, label }}
					<a {href} class="transition hover:text-gray-300">{label}</a>
				{/each}

				<a
					href="https://github.com/Narendrakumar-Suresh/Seraphic"
					target="_blank"
					rel="noopener noreferrer"
					aria-label="github-link"
				>
					<GithubLogo />
				</a>
			</div>

			<button class="rounded-2xl border-2 px-4 py-2"><a href="/auth">Login</a></button>

			<button
				type="button"
				class="rounded-md p-2 hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-500 md:hidden"
				aria-controls="mobile-menu"
				aria-expanded={isOpen}
				on:click={toggleMenu}
			>
				<span class="sr-only">Open main menu</span>
				{#if isOpen}
					<!-- Close Icon -->
					<svg
						class="h-6 w-6"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						viewBox="0 0 24 24"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
					</svg>
				{:else}
					<!-- Menu Icon -->
					<svg
						class="h-6 w-6"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						viewBox="0 0 24 24"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
					</svg>
				{/if}
			</button>
		</div>
	</nav>

	<!-- Mobile menu -->
	{#if isOpen}
		<div id="mobile-menu" class="md:hidden" transition:fly={{ y: -20, duration: 300 }}>
			<div class="flex flex-col space-y-1 bg-transparent px-4 py-3 text-white sm:px-6">
				{#each navItems as { href, label }}
					<a {href} class="block rounded-md px-4 py-2 hover:bg-gray-800">{label}</a>
				{/each}
			</div>
		</div>
	{/if}
</header>

<!-- Spacer to prevent content from going under fixed header -->
<!-- <div class="h-16"></div> -->
