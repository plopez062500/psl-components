<script lang="ts" context="module">
	export type Size = keyof typeof sizes;
	export const sizes = {
		fit: 'w-fit',
		sm: 'w-[400px]',
		md: 'w-[600px]',
		lg: 'w-[800px]',
		full: 'w-full'
	};
</script>

<script lang="ts">
	import { slide } from 'svelte/transition';

	export let size: Size = 'sm';

	let open: boolean = false;
	function toggle_state() {
		open = !open;
	}
</script>

<div class={`p-1.5 border rouded-sm ${sizes[size]}`}>
	<div class="flex justify-between">
		<slot name="title">Header</slot>
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<!-- svelte-ignore a11y-no-static-element-interactions -->
		<svg
			class="cursor-pointer transition-all"
			class:-rotate-180={!open}
			width="20px"
			viewBox="0 0 330 330"
			on:click={toggle_state}
		>
			<path
				id="XMLID_224_"
				d="M325.606,229.393l-150.004-150C172.79,76.58,168.974,75,164.996,75c-3.979,0-7.794,1.581-10.607,4.394  l-149.996,150c-5.858,5.858-5.858,15.355,0,21.213c5.857,5.857,15.355,5.858,21.213,0l139.39-139.393l139.397,139.393  C307.322,253.536,311.161,255,315,255c3.839,0,7.678-1.464,10.607-4.394C331.464,244.748,331.464,235.251,325.606,229.393z"
			/>
		</svg>
	</div>

	{#if open}
		<div transition:slide>
			<slot name="body">No Content Provided</slot>
		</div>
	{/if}
</div>
