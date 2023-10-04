<script lang="ts" context="module">
	export type Size = keyof typeof sizes;
	export const sizes = {
		sm: 'px-2 py-1',
		md: 'px-2 py-2',
		lg: 'px-2 py-3 text-xl'
	};

	export type InputType = 'text' | 'password' | 'number';
</script>

<script lang="ts">
	export let full_width: boolean = false;
	export let size: Size = 'md';

	export let type: InputType = 'password';
	export let name: string;
	export let label: string = name;
	export let placeholder: string = name;
	export let value: string = '';
	export let min: number = Number.MIN_SAFE_INTEGER;
	export let max: number = Number.MAX_SAFE_INTEGER;
</script>

<label>
	{label}
	{#if type === 'text'}
		<input
			class={`${sizes[size]} border border-gray-300 rounded-sm outline-blue-300  transition-all block`}
			class:w-full={full_width}
			{name}
			{placeholder}
			bind:value
		/>
	{/if}

	{#if type === 'password'}
		<input
			class={`${sizes[size]} border border-gray-300 rounded-sm outline-blue-300  transition-all block`}
			class:w-full={full_width}
			type='password'
			{name}
			{placeholder}
			bind:value
		/>
	{/if}

	{#if type === 'number'}
		<input
			class={`${sizes[size]} border border-gray-300 rounded-sm outline-blue-300  transition-all block`}
			class:w-full={full_width}
			type="number"
			{name}
			{placeholder}
			{min}
			{max}
			bind:value
		/>
	{/if}
</label>
