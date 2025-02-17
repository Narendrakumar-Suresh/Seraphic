<script>
	import { fly } from 'svelte/transition';

	let isOpen = false;

	// Navigation items
	const navItems = [
		{ href: '/', label: 'Home' },
		{ href: '/about', label: 'About' },
		{ href: '/services', label: 'Services' },
		{ href: '/contact', label: 'Contact' }
	];

	// Toggle mobile menu
	function toggleMenu() {
		isOpen = !isOpen;
	}
</script>

<header class="fixed top-0 z-50 w-full bg-black text-white shadow-sm">
	<nav class="container mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex h-16 items-center justify-between">
			<!-- Logo/Brand -->
			<div class="flex flex-shrink-0 items-center">
				<a href="/" class="text-xl font-bold"> CRACK </a>
			</div>

			<!-- Desktop Navigation -->
			<div class="hidden items-center space-x-8 md:flex">
				{#each navItems as { href, label }}
					<a {href}>{label}</a>
				{/each}
			</div>

			<!-- Mobile menu button -->
			<div class="md:hidden">
				<button
					type="button"
					class="focus:ring-primary inline-flex items-center justify-center rounded-md p-2 text-gray-600 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-inset"
					aria-controls="mobile-menu"
					aria-expanded={isOpen}
					on:click={toggleMenu}
				>
					<span class="sr-only">Open main menu</span>
					<!-- Icon when menu is closed -->
					<svg
						class="h-6 w-6 {isOpen ? 'hidden' : 'block'}"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/>
					</svg>
					<!-- Icon when menu is open -->
					<svg
						class="h-6 w-6 {isOpen ? 'block' : 'hidden'}"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					</svg>
				</button>
			</div>
		</div>
	</nav>

	<!-- Mobile menu -->
	{#if isOpen}
		<div id="mobile-menu" class="md:hidden" transition:fly={{ y: -20, duration: 500 }}>
			<div class="flex flex-col space-y-1 bg-black px-2 pb-3 pt-2 text-white sm:px-3">
				{#each navItems as { href, label }}
					<a {href}>{label}</a>
				{/each}
			</div>
		</div>
	{/if}
</header>

<!-- Spacer to prevent content from going under fixed header -->
<div class="h-16"></div>
