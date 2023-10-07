<script lang="ts" context="module">
	export type Color = keyof typeof colors;
	export type Variant = keyof (typeof colors)[Color];
	export const colors = {
		blue: {
			filled:
				'bg-blue-500 text-white border-blue-500 hover:text-blue-500 hover:bg-white border border-blue-500',
			outline:
				'bg-white text-blue-500 border-blue-500 hover:text-white hover:bg-blue-500 border border-blue-500',
			ghost: 'bg-white text-blue-500 border-blue-500 hover:text-white hover:bg-blue-500'
		},
		red: {
			filled:
				'bg-red-500 text-white border-red-500 hover:text-red-500 hover:bg-white border border-red-500',
			outline:
				'bg-white text-red-500 border-red-500 hover:text-white hover:bg-red-500 border border-red-500',
			ghost: 'bg-white text-red-500 border-red-500 hover:text-white hover:bg-red-500'
		},
		green: {
			filled:
				'bg-green-500 text-white border-green-500 hover:text-green-500 hover:bg-white border border-green-500',
			outline:
				'bg-white text-green-500 border-green-500 hover:text-white hover:bg-green-500 border border-green-500',
			ghost: 'bg-white text-green-500 border-green-500 hover:text-white hover:bg-green-500'
		},
		yellow: {
			filled:
				'bg-yellow-300 text-white border-yellow-300 hover:text-yellow-300 hover:bg-white border border-yellow-300',
			outline:
				'bg-white text-yellow-500 border-yellow-500 hover:text-white hover:bg-yellow-500 border border-yellow-500',
			ghost: 'bg-white text-yellow-500 border-yellow-500 hover:text-white hover:bg-yellow-500'
		},
		gray: {
			filled:
				'bg-gray-300 text-white border-gray-300 hover:text-gray-300 hover:bg-white border border-gray-300',
			outline:
				'bg-white text-gray-500 border-gray-500 hover:text-white hover:bg-gray-500 border border-gray-500',
			ghost: 'bg-white text-gray-500 border-gray-500 hover:text-white hover:bg-gray-500'
		}
	};

	export type Size = keyof typeof sizes;
	export const sizes = {
		sm: 'px-4 py-1',
		md: 'px-6 py-2',
		lg: 'px-8 py-3'
	};
</script>

<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let full_width: boolean = false;
	export let color: Color = 'blue';
	export let variant: Variant = 'filled';
	export let size: Size = 'md';

	const dispatch = createEventDispatcher();

	function on_click(event: any) {
		dispatch('click', event.detail);
	}

    $: misc_props = $$props;
</script>

<button
	class={`${sizes[size]} ${colors[color][variant]} transition-all rounded-sm h-fit`}
	class:w-full={full_width}
	on:click={on_click}
    {...misc_props}
	><slot />
</button>
