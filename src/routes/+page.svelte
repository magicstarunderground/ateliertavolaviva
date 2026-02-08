<script lang="ts">
	import { fade } from 'svelte/transition';
	import SectionHeading from '$components/SectionHeading.svelte';
	import MenuCard from '$components/MenuCard.svelte';
	import content from '$lib/data/content.json';
	import menusData from '$lib/data/menus.json';

	// Hero section images
	import heroImg from '$lib/assets/almaphotographyalma-7_1769639427309.jpg';
	import portraitImg from '$lib/assets/retrato_1768838009913.webp';
	import impactImg from '$lib/assets/hojas_1768838009906.webp';
	import workshopImg from '$lib/assets/manchas_1768838009910.webp';
	import nourishImg from '$lib/assets/img_9254_1769769809014.jpg';

	// Menu images
	import menu1Img from '$lib/assets/bowl__1768838009902.webp';
	import menu2Img from '$lib/assets/picada_1768838009912.webp';
	import menu3Img from '$lib/assets/cuadrados_1768838009904.webp';
	import menu4Img from '$lib/assets/plato_1768838009912.webp';

	// Add images to menus
	const menus = menusData.map((menu, index) => {
		const images = [menu1Img, menu2Img, menu3Img, menu4Img];
		return { ...menu, imageUrl: images[index] };
	});

	let formData = {
		name: '',
		email: '',
		subject: '',
		message: ''
	};

	let isSubmitting = false;

	async function handleSubmit() {
		isSubmitting = true;
		console.log('Form submission:', formData);
		// Simulate a small delay
		await new Promise((resolve) => setTimeout(resolve, 500));
		formData = { name: '', email: '', subject: '', message: '' };
		isSubmitting = false;
		console.log('Form reset');
	}
</script>

<svelte:head>
	<title>Atelier Tavola Viva - Art & Gastronomy</title>
</svelte:head>

<div class="min-h-screen font-sans selection:bg-terracotta/30">

	<!-- ===== HERO SECTION ===== -->
	<section class="relative flex min-h-[800px] items-center justify-center overflow-hidden h-screen">
		<!-- Background with overlay -->
		<div class="absolute inset-0 z-0">
			<img src={heroImg} alt="Artistic photography of a Patagonia landscape" class="h-full w-full object-cover" />
			<div class="absolute inset-0 bg-black/40 backdrop-blur-[2px]" />
		</div>

		<!-- Content -->
		<div class="container relative z-10 mx-auto max-w-4xl px-4 text-center text-white">
			<p
				class="mb-6 text-sm uppercase tracking-[0.3em] text-white/90 md:text-base"
				in:fade={{ duration: 800, delay: 200 }}
				out:fade
			>
				{content.hero.subtitle}
			</p>

			<h1
				class="mb-8 font-display text-5xl font-medium leading-tight drop-shadow-lg md:text-7xl lg:text-8xl"
				in:fade={{ duration: 1000 }}
				out:fade
			>
				Connecting on the <br />
				<span class="italic font-normal text-white/90">{content.hero.titleItalic}</span>
			</h1>

			<p
				class="mx-auto max-w-2xl text-lg font-light leading-relaxed text-white/80 md:text-xl"
				in:fade={{ duration: 800, delay: 600 }}
				out:fade
			>
				{content.hero.description}
			</p>

			<div
				class="mt-12"
				in:fade={{ duration: 800, delay: 1000 }}
				out:fade
			>
				<a
					href="#menus"
					class="inline-block rounded-full border border-white/30 bg-white/10 px-8 py-4 font-medium tracking-wide text-white backdrop-blur-sm transition-all duration-300 hover:bg-white hover:text-foreground"
				>
					Discover the Experience
				</a>
			</div>
		</div>

		<!-- Scroll indicator -->
		<div
			class="absolute bottom-10 left-1/2 -translate-x-1/2 text-white/50"
			in:fade={{ duration: 800 }}
			out:fade
		>
			<span class="text-[10px] uppercase tracking-widest">Scroll</span>
		</div>
	</section>

	<!-- ===== STORY SECTION ===== -->
	<section id="story" class="relative overflow-hidden bg-white py-24 md:py-32">
		<div class="absolute top-0 right-0 -translate-x-1/3 skew-x-12 h-full w-1/3 bg-water-green/20"></div>

		<div class="container relative z-10 mx-auto px-4">
			<div class="grid grid-cols-1 gap-16 items-center lg:grid-cols-2 lg:gap-24">
				<!-- Image -->
				<div class="relative" in:fade={{ duration: 800 }} out:fade>
					<div class="relative z-10 overflow-hidden rounded-lg shadow-2xl">
						<img
							src={portraitImg}
							alt="Alma, visual artist and private chef, founder of Atelier Tavola Viva"
							class="aspect-[3/4] w-full object-cover"
						/>
					</div>
					<div class="absolute -bottom-8 -left-8 h-64 w-64 rounded-full bg-terracotta/10 blur-3xl"></div>
					<div class="absolute -top-8 -right-8 h-40 w-40 rounded-full border border-terracotta/30"></div>
				</div>

				<!-- Content -->
				<div>
					<SectionHeading subtitle={content.story.subtitle} align="left">
						Alma: From Patagonia <br /> to the World
					</SectionHeading>

					<div class="space-y-6" in:fade={{ duration: 800, delay: 200 }} out:fade>
						{#each content.story.paragraphs as paragraph}
							<p class="font-light leading-relaxed text-lg text-muted-foreground">
								{paragraph}
							</p>
						{/each}
					</div>

					<div class="mt-10 flex gap-4">
						{#each content.story.stats as stat}
							<div class="flex flex-col">
								<span class="font-display text-4xl text-terracotta">{stat.value}</span>
								<span class="mt-1 text-xs uppercase tracking-widest text-muted-foreground">{stat.label}</span>
							</div>
							{#if stat !== content.story.stats[content.story.stats.length - 1]}
							<div class="mx-4 h-12 w-px bg-border"></div>
							{/if}
						{/each}
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- ===== IMPACT SECTION ===== -->
	<section id="impact" class="relative bg-muted/30 py-24 md:py-32">
		<div class="container mx-auto max-w-6xl px-4">
			<SectionHeading subtitle={content.impact.subtitle}>
				{content.impact.title}
			</SectionHeading>

			<!-- Main Impact content -->
			<div class="mb-8 flex flex-col gap-12 rounded-3xl bg-white p-8 shadow-xl shadow-black/5 md:p-12 md:grid md:grid-cols-2 md:items-center">
				<div class="space-y-6" in:fade={{ duration: 800 }} out:fade>
					<h3 class="text-3xl font-display font-medium text-foreground">
						{content.impact.mainContent.heading}
					</h3>
					{#each content.impact.mainContent.paragraphs as para}
						<p class="leading-relaxed text-muted-foreground">
							{para}
						</p>
					{/each}
				</div>
				<div class="relative h-80 overflow-hidden rounded-2xl shadow-lg md:h-full md:min-h-[400px]">
					<img
						src={nourishImg}
						alt="Nature texture and organic details representing conscious gastronomy philosophy"
						class="absolute inset-0 h-full w-full scale-150 rotate-90 object-cover transition-transform duration-700 group-hover:scale-[1.6]"
					/>
				</div>
			</div>

			<!-- Sustainability -->
			<div class="rounded-3xl bg-white p-8 shadow-xl shadow-black/5 md:p-12">
				<div class="mx-auto mb-12 max-w-3xl text-center">
					<h3 class="mb-4 font-display text-3xl font-medium text-foreground">
						{content.impact.sustainability.heading}
					</h3>
					<p class="leading-relaxed text-muted-foreground">
						{content.impact.sustainability.description}
					</p>
				</div>
				<div class="grid grid-cols-1 gap-8 md:grid-cols-3">
					{#each content.impact.sustainability.items as item}
						<div class="space-y-3">
							<h4 class="font-display text-xl font-medium text-terracotta">{item.heading}</h4>
							<p class="text-sm leading-relaxed text-muted-foreground">
								{item.description}
							</p>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<!-- ===== MENUS SECTION ===== -->
	<section id="menus" class="bg-background py-24 md:py-32">
		<div class="container mx-auto px-4">
			<SectionHeading subtitle={content.workshops.subtitle}>
				{content.workshops.description ? content.impact.title : 'Curated Culinary Journeys'}
			</SectionHeading>

			<div class="mt-12 grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4 lg:gap-8">
				{#each menus as menu, index (menu.id)}
					<MenuCard {menu} {index} />
				{/each}
			</div>
		</div>
	</section>

	<!-- ===== WORKSHOPS SECTION ===== -->
	<section id="workshops" class="relative overflow-hidden py-24 md:py-32">
		<div class="absolute inset-0">
			<img
				src={impactImg}
				alt="Artistic textures representing the creative workshop environment"
				class="h-full w-full object-cover"
			/>
			<div class="absolute inset-0 bg-black/60" />
		</div>

		<div class="container relative z-10 mx-auto px-4">
			<div class="mx-auto max-w-4xl text-center">
				<SectionHeading light subtitle={content.workshops.subtitle}>
					{content.workshops.title}
				</SectionHeading>

				<p class="mb-12 text-xl leading-relaxed text-black/90 md:text-2xl">
					{content.workshops.description}
				</p>

				<div class="mx-auto max-w-3xl grid grid-cols-1 gap-8 text-left sm:grid-cols-2">
					{#each content.workshops.types as type}
						<div class="rounded-2xl border border-white/10 bg-white p-8 transition-colors hover:bg-white/95 backdrop-blur-sm text-black">
							<div
								class="mb-6 flex h-12 w-12 items-center justify-center rounded-full border border-white/20 bg-white text-black font-display text-xs uppercase tracking-tighter"
							>
								{type.acronym}
							</div>
							<h3 class="mb-3 font-display text-2xl text-black">{type.heading}</h3>
							<p class="font-light text-black/80">
								{type.description}
							</p>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<!-- ===== CONTACT SECTION ===== -->
	<section id="contact" class="bg-background py-24 md:py-32">
		<div class="container mx-auto max-w-5xl px-4">
			<div class="grid grid-cols-1 gap-16 lg:grid-cols-2">
				<!-- Contact Info -->
				<div in:fade={{ duration: 800 }} out:fade>
					<SectionHeading subtitle={content.contact.subtitle} align="left">
						{content.contact.title}
					</SectionHeading>
					<p class="mb-8 text-lg font-light text-muted-foreground">
						{content.contact.description}
					</p>

					<div class="mt-12 space-y-6">
						<div class="flex gap-4 items-center">
							<div class="flex h-12 w-12 items-center justify-center rounded-full bg-secondary/30 text-secondary-foreground">
								📧
							</div>
							<div>
								<p class="text-sm uppercase tracking-widest text-muted-foreground">Email</p>
								<p class="text-lg font-medium">{content.contact.email}</p>
							</div>
						</div>
						<div class="flex gap-4 items-center">
							<div class="flex h-12 w-12 items-center justify-center rounded-full bg-secondary/30 text-secondary-foreground">
								📍
							</div>
							<div>
								<p class="text-sm uppercase tracking-widest text-muted-foreground">Location</p>
								<p class="text-lg font-medium">{content.contact.location}</p>
							</div>
						</div>
					</div>
				</div>

			</div>
		</div>
	</section>

	<!-- ===== FOOTER ===== -->
	<footer class="border-t border-white/10 bg-foreground py-16 text-white/40">
		<div class="container mx-auto px-4">
			<div class="mb-12 flex flex-col items-start gap-12 md:flex-row md:justify-between">
				<!-- Branding -->
				<div class="text-left">
					<span class="mb-1 block font-display text-2xl text-white">Atelier Tavola Viva</span>
					<span class="text-xs uppercase tracking-widest">Art & Gastronomy</span>
				</div>

				<!-- Partners -->
				<div class="space-y-4">
					<span class="block text-xs uppercase tracking-widest text-white/60">Our Partners</span>
					<div class="flex flex-col gap-4 sm:flex-row">
						{#each content.footer.partners as partner}
							<a
								href={partner.url}
								target="_blank"
								rel="noopener noreferrer"
								class="group flex flex-1 gap-3 rounded-xl border border-white/10 bg-white/5 p-4 transition-all hover:bg-white/10"
							>
								<div class="flex h-8 w-8 items-center justify-center text-white">
									{#if partner.name === 'Airbnb Experiences'}
										<svg viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg" class="h-full w-full fill-current">
											<path d="M16 1c2.008 0 3.463.963 4.751 3.269l.533 1.025c1.954 3.83 6.114 12.54 7.1 14.836l.145.353c.667 1.591.91 2.472.96 3.396l.01.415.001.228c0 4.062-2.877 6.478-6.357 6.478-2.224 0-4.556-1.258-6.709-3.386l-.257-.26-.172-.179h-.011l-.176.185c-2.044 2.1-4.392 3.415-6.401 3.631l-.28.012c-3.535 0-6.423-2.367-6.423-6.502 0-1.296.297-2.548.832-4.118l.171-.491c.391-.1.391-.1.419-.115.158-.088.35-.2.536-.334l.217-.16c1.192-3.085 4.966-10.741 7.217-15.195l.533-1.025C12.537 1.963 13.992 1 16 1zm0 2c-1.232 0-2.046.593-3.039 2.392l-.533 1.025c-2.33 4.607-6.22 12.512-7.397 15.602l-.116.326c-.46 1.341-.703 2.378-.737 3.167l-.008.272c0 2.923 1.944 4.502 4.423 4.502 1.623 0 3.606-1.127 5.485-3.078l.255-.27.114-.122c.263-.284.697-.284.96 0l.115.122.256.27c1.935 2.011 3.983 3.078 5.66 3.078 2.433 0 4.357-1.637 4.357-4.478 0-.756-.192-1.503-.615-2.523l-.11-.264c-.954-2.22-5.118-10.932-7.072-14.764l-.533-1.025C18.046 3.593 17.232 3 16 3z" />
										</svg>
									{:else if partner.name === 'Private Chef'}
										<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" class="h-full w-full fill-none stroke-current stroke-2">
											<path d="M6 13.847c0 3.153 2.686 5.71 6 5.71s6-2.557 6-5.71V8c0-3.314-2.686-6-6-6S6 4.686 6 8v5.847zM12 2v6" />
											<path d="M12 19.557v2.443M9 22h6" />
										</svg>
									{:else}
										<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" class="h-full w-full fill-current">
											<path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.414 0 .01 5.403.007 12.039c0 2.12.54 4.189 1.571 6.04L0 24l6.102-1.6c1.79.976 3.805 1.491 5.86 1.493h.005c6.634 0 12.04-5.404 12.042-12.041 0-3.216-1.252-6.241-3.526-8.514z" />
										</svg>
									{/if}
								</div>
								<div>
									<p class="text-sm font-medium text-white">{partner.name}</p>
									<p class="text-[10px] uppercase tracking-widest text-white/40">{partner.description}</p>
								</div>
							</a>
						{/each}
					</div>
				</div>
			</div>

			<!-- Bottom Footer -->
			<div class="flex flex-col items-center gap-6 border-t border-white/10 pt-12 md:flex-row md:justify-between">
				<div class="text-sm">
					&copy; {new Date().getFullYear()} All rights reserved.
				</div>
				<div class="flex gap-6">
					{#each content.footer.social as link}
						<a href={link.url} class="transition-colors hover:text-terracotta">
							{link.name}
						</a>
					{/each}
				</div>
			</div>
		</div>
	</footer>
</div>
