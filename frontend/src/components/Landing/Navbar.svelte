<script>
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
			<!-- Logo/Brand -->
			<a href="/" class="text-2xl font-bold"> SERAPHIC </a>

			<!-- Desktop Navigation -->
			<!-- <div class="w-full justify-between bg-green-200"> -->
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
					<svg
						class="h-8 w-8 transition hover:opacity-80"
						viewBox="0 0 256 250"
						fill="currentColor"
						xmlns="http://www.w3.org/2000/svg"
						preserveAspectRatio="xMidYMid"
					>
						<path
							d="M128.001 0C57.317 0 0 57.307 0 128.001c0 56.554 36.676 104.535 87.535 121.46 6.397 1.185 8.746-2.777 8.746-6.158 0-3.052-.12-13.135-.174-23.83-35.61 7.742-43.124-15.103-43.124-15.103-5.823-14.795-14.213-18.73-14.213-18.73-11.613-7.944.876-7.78.876-7.78 12.853.902 19.621 13.19 19.621 13.19 11.417 19.568 29.945 13.911 37.249 10.64 1.149-8.272 4.466-13.92 8.127-17.116-28.431-3.236-58.318-14.212-58.318-63.258 0-13.975 5-25.394 13.188-34.358-1.329-3.224-5.71-16.242 1.24-33.874 0 0 10.749-3.44 35.21 13.121 10.21-2.836 21.16-4.258 32.038-4.307 10.878.049 21.837 1.47 32.066 4.307 24.431-16.56 35.165-13.12 35.165-13.12 6.967 17.63 2.584 30.65 1.255 33.873 8.207 8.964 13.173 20.383 13.173 34.358 0 49.163-29.944 59.988-58.447 63.157 4.591 3.972 8.682 11.762 8.682 23.704 0 17.126-.148 30.91-.148 35.126 0 3.407 2.304 7.398 8.792 6.14C219.37 232.5 256 184.537 256 128.002 256 57.307 198.691 0 128.001 0Z"
						/>
					</svg>
				</a>
			</div>

			Login
			<!-- </div> -->

			<!-- Mobile menu button -->
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
