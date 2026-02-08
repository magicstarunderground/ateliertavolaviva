<script lang="ts">
	import { fade } from 'svelte/transition';

	interface Menu {
		id: number;
		title: string;
		description: string;
		category: string;
		imageUrl: string;
	}

	interface Props {
		menu: Menu;
		index: number;
	}

	let { menu, index }: Props = $props();
</script>

<div
	class="group relative flex h-full flex-col overflow-hidden rounded-xl border border-border/40 bg-white shadow-lg transition-all duration-500 hover:shadow-xl"
	in:fade={{ duration: 600, delay: index * 100 }}
	out:fade
>
	<div class="relative h-64 overflow-hidden">
		<div class="absolute inset-0 z-10 bg-black/10 transition-colors group-hover:bg-black/0" />
		{#if menu.imageUrl}
			<img
				src={menu.imageUrl}
				alt={menu.title}
				class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
			/>
		{:else}
			<div class="flex h-full w-full items-center justify-center bg-muted text-muted-foreground">
				No Image
			</div>
		{/if}
		<div class="absolute top-4 left-4 z-20">
			<span
				class="rounded-full bg-white/90 px-3 py-1 text-xs font-semibold uppercase tracking-wider text-foreground shadow-sm backdrop-blur-sm"
			>
				{menu.category?.replace('_', ' ')}
			</span>
		</div>
	</div>

	<div class="flex flex-grow flex-col p-8">
		<h3 class="mb-3 font-display text-2xl font-bold text-foreground transition-colors group-hover:text-terracotta">
			{menu.title}
		</h3>
		<p class="flex-grow font-light leading-relaxed text-muted-foreground">
			{menu.description}
		</p>


	</div>
</div>
