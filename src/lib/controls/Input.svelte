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
	export let extendable_right: boolean = false;
	export let extendable_left: boolean = false;

	export let type: InputType = 'text';
	export let name: string;
	export let label: string = name;
	export let placeholder: string = name;
	export let value: string = '';
	export let min: number = Number.MIN_SAFE_INTEGER;
	export let max: number = Number.MAX_SAFE_INTEGER;
	export let readonly: boolean = false;
</script>

<label>
	{label}
	{#if type === 'text'}
		<input
			class={`${sizes[size]} border border-gray-300 rounded-sm outline-blue-300  transition-all block`}
			class:w-full={full_width}
			class:border-r-0={extendable_right}
			class:border-l-0={extendable_left}
			{name}
			{placeholder}
			{readonly}
			bind:value
		/>
	{/if}

	{#if type === 'password'}
		<input
			class={`${sizes[size]} border border-gray-300 rounded-sm outline-blue-300  transition-all block`}
			class:w-full={full_width}
			class:border-r-0={extendable_right}
			class:border-l-0={extendable_left}
			type='password'
			{name}
			{placeholder}
			{readonly}
			bind:value
		/>
	{/if}

	{#if type === 'number'}
		<input
			class={`${sizes[size]} border border-gray-300 rounded-sm outline-blue-300  transition-all block`}
			class:w-full={full_width}
			class:border-r-0={extendable_right}
			class:border-l-0={extendable_left}
			type="number"
			{name}
			{placeholder}
			{readonly}
			{min}
			{max}
			bind:value
		/>
	{/if}
</label>
