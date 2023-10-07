<script lang="ts">
	import { slide } from 'svelte/transition';
	import Input from './Input.svelte';

	export let name: string;
	export let label: string = 'Label';
	export let items: string[];
	export let default_text: string = '-- Select --';
	export let value: string = default_text;
	export let max_visible_options = 5;

	if (items.length < 1) throw new Error('Select Component must have one or more items');

	let max_options_window_heigth = 40 * max_visible_options;
	let show_options = false;

	function toggle_show_options() {
		show_options = !show_options;
	}

	function select_item(index: number) {
		if (index < 0 || index > items.length - 1) return;
		value = items[index];
		toggle_show_options();
	}
</script>

<div class="relative">
	<!-- Selected Option Control -->
	<div class="flex items-center justify-center">
		<Input readonly {name} {label} bind:value extendable_right />

		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<!-- svelte-ignore a11y-no-static-element-interactions -->
		<div
			class="flex items-center justify-center self-end h-[42px] p-2 bg-gray-100 border border-gray-300 border-l-0"
			on:click={toggle_show_options}
		>
			<svg class="cursor-pointer transition-all -rotate-180" class:-rotate-180={!show_options} width="20px" viewBox="0 0 330 330">
				<path
					id="XMLID_224_"
					d="M325.606,229.393l-150.004-150C172.79,76.58,168.974,75,164.996,75c-3.979,0-7.794,1.581-10.607,4.394  l-149.996,150c-5.858,5.858-5.858,15.355,0,21.213c5.857,5.857,15.355,5.858,21.213,0l139.39-139.393l139.397,139.393  C307.322,253.536,311.161,255,315,255c3.839,0,7.678-1.464,10.607-4.394C331.464,244.748,331.464,235.251,325.606,229.393z"
				/>
			</svg>
		</div>
	</div>

	<!-- Options Menu -->
	{#if show_options}
		<div
			class={`flex flex-col bg-white border absolute w-full options-window`}
			style="--option_window_height: {max_options_window_heigth}px;"
			transition:slide
		>
			{#each items as item, i}
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<div
					class=" p-2 cursor-pointer hover:bg-blue-500 hover:text-white transition-all"
					on:click={() => {
						select_item(i);
					}}
				>
					{item}
				</div>
			{/each}
		</div>
	{/if}
</div>

<style>
	.options-window {
		max-height: var(--option_window_height);
		overflow-y: scroll;
	}

	.options-window::-webkit-scrollbar {
		width: 10px;
	}

	.options-window::-webkit-scrollbar-track {
		background-color: white;
	}

	.options-window::-webkit-scrollbar-thumb {
		background: #ddd;
		border-radius: 100px;
	}
</style>
