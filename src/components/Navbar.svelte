<script lang="ts">
	import { onMount } from 'svelte';
	import { slide } from 'svelte/transition';

	let isScrolled = false;
	let isMobileMenuOpen = false;

	const navLinks = [
		{ name: 'Story', href: '#story' },
		{ name: 'Impact', href: '#impact' },
		{ name: 'Menus', href: '#menus' },
		{ name: 'Workshops', href: '#workshops' },
		{ name: 'Contact', href: '#contact' }
	];

	onMount(() => {
		const handleScroll = () => {
			isScrolled = window.scrollY > 50;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function handleScrollTo(e: Event, id: string) {
		e.preventDefault();
		isMobileMenuOpen = false;
		const element = document.getElementById(id.replace('#', ''));
		if (element) {
			element.scrollIntoView({ behavior: 'smooth' });
		}
	}
</script>

<header
	class={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 border-b ${
		isScrolled
			? 'bg-background/80 backdrop-blur-md py-4 shadow-sm border-border/50'
			: 'bg-transparent py-6 border-transparent'
	}`}
>
	<div class="container mx-auto flex items-center justify-between px-4 sm:px-6 lg:px-8">
		<!-- Logo -->
		<a href="/" class="relative z-50">
			<div class="flex flex-col">
				<span
					class={`font-display text-2xl font-bold tracking-tight transition-colors ${
						isScrolled || isMobileMenuOpen ? 'text-foreground' : 'text-white'
					}`}
				>
					Atelier Tavola Viva
				</span>
				<span
					class={`text-[10px] uppercase tracking-widest transition-colors ${
						isScrolled || isMobileMenuOpen ? 'text-muted-foreground' : 'text-white/80'
					}`}
				>
					Art & Gastronomy
				</span>
			</div>
		</a>

		<!-- Desktop Navigation -->
		<nav class="hidden space-x-8 md:flex md:items-center">
			{#each navLinks as link (link.name)}
				<a
					href={link.href}
					on:click={(e) => handleScrollTo(e, link.href)}
					class={`group relative py-2 text-sm font-medium tracking-wide transition-colors hover:text-terracotta ${
						isScrolled ? 'text-foreground/80' : 'text-white/90'
					}`}
				>
					{link.name}
					<span
						class="absolute bottom-0 left-0 h-px w-full scale-x-0 origin-left bg-terracotta transition-transform duration-300 group-hover:scale-x-100"
					></span>
				</a>
			{/each}
		</nav>

		<!-- Mobile Menu Button -->
		<button
			class="relative z-50 p-2 md:hidden"
			on:click={() => (isMobileMenuOpen = !isMobileMenuOpen)}
			aria-label="Toggle menu"
		>
			{#if isMobileMenuOpen}
				<svg class="h-6 w-6 text-foreground" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
				</svg>
			{:else}
				<svg
					class={`h-6 w-6 ${isScrolled ? 'text-foreground' : 'text-white'}`}
					fill="none"
					stroke="currentColor"
					viewBox="0 0 24 24"
				>
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
				</svg>
			{/if}
		</button>
	</div>

	<!-- Mobile Menu -->
	{#if isMobileMenuOpen}
		<div
			transition:slide
			class="border-t border-border/50 bg-background/95 backdrop-blur-md md:hidden"
		>
			<nav class="container mx-auto flex flex-col gap-1 px-4 py-4">
				{#each navLinks as link (link.name)}
					<a
						href={link.href}
						on:click={(e) => handleScrollTo(e, link.href)}
						class="px-4 py-3 text-foreground/80 transition-colors hover:bg-secondary/30 hover:text-terracotta"
					>
						{link.name}
					</a>
				{/each}
			</nav>
		</div>
	{/if}
</header>

