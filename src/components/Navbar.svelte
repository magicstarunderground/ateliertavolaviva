<script lang="ts">
	let isOpen = $state(false);

	function toggleMenu() {
		isOpen = !isOpen;
	}

	function closeMenu() {
		isOpen = false;
	}

	const navLinks = [
		{ label: 'Home', href: '#hero' },
		{ label: 'About', href: '#about' },
		{ label: 'Philosophy', href: '#philosophy' },
		{ label: 'Offerings', href: '#offerings' },
		{ label: 'Experiences', href: '#experiences' },
		{ label: 'Contact', href: '#contact' }
	];
</script>

<nav class="top-0 z-50 w-full bg-white/95 backdrop-blur-md shadow-md">
	<div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
		<!-- Logo -->
		<a href="#hero" on:click={closeMenu} class="text-xl font-light tracking-wide text-gray-900 hover:text-orange-500 transition-colors">
			Atelier Tavola Viva
		</a>

		<!-- Desktop Menu -->
		<div class="hidden md:flex items-center space-x-8">
			{#each navLinks as link}
				<a
					href={link.href}
					class="text-gray-700 hover:text-orange-500 transition-colors font-light text-sm tracking-wide"
				>
					{link.label}
				</a>
			{/each}
		</div>

		<!-- Mobile Menu Button -->
		<button
			on:click={toggleMenu}
			class="md:hidden p-2 hover:bg-gray-100 rounded-lg transition-colors"
			aria-label="Toggle menu"
		>
			<svg
				class="w-6 h-6 text-gray-900"
				fill="none"
				stroke="currentColor"
				viewBox="0 0 24 24"
			>
				{#if isOpen}
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
				{:else}
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
				{/if}
			</svg>
		</button>
	</div>

	<!-- Mobile Menu -->
	{#if isOpen}
		<div
			class="md:hidden bg-white border-t border-gray-200 py-4 px-6 space-y-4 animate-in fade-in slide-in-from-top-2 duration-200"
		>
			{#each navLinks as link}
				<a
					href={link.href}
					on:click={closeMenu}
					class="block text-gray-700 hover:text-orange-500 transition-colors font-light uppercase tracking-wide"
				>
					{link.label}
				</a>
			{/each}
		</div>
	{/if}
</nav>

<style>
	:global(html) {
		scroll-behavior: smooth;
	}
</style>
