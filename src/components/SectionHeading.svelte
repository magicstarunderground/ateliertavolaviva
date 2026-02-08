<script lang="ts">
	import { fade } from 'svelte/transition';

	interface Props {
		children?: any;
		subtitle?: string;
		align?: 'left' | 'center' | 'right';
		light?: boolean;
	}

	let { children, subtitle, align = 'center', light = false }: Props = $props();

	const alignmentClass =
		align === 'left'
			? 'text-left'
			: align === 'right'
				? 'text-right'
				: 'text-center';
</script>

<div class={`mb-12 flex flex-col gap-3 md:mb-16 ${alignmentClass}`}>
	{#if subtitle}
		<span
			class={`text-sm font-medium uppercase tracking-[0.2em] ${
				light ? 'text-black/80' : 'text-terracotta'
			}`}
			in:fade={{ duration: 600 }}
			out:fade
		>
			{subtitle}
		</span>
	{/if}
	<h2
		class={`text-3xl font-display font-medium leading-tight md:text-5xl lg:text-6xl ${
			light ? 'text-black' : 'text-black'
		}`}
		in:fade={{ duration: 600, delay: 100 }}
		out:fade
	>
		{@render children?.()}
	</h2>
</div>
