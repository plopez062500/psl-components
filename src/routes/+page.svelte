<script>
	import Button from "$lib/controls/Button.svelte";

</script>

<section>
	<h1 class="text-3xl">Buttons</h1>

	<h3 class="text-xl">Variants</h3>
	<seciton class="flex gap-3">
		<Button>Filled</Button>
		<Button variant='outline'>Outline</Button>
		<Button variant='ghost'>Ghost</Button>
	</seciton>

	<h3 class="text-xl">Sizes</h3>
	<seciton class="flex gap-3 items-center">
		<Button size='sm'>Small</Button>
		<Button>Medium</Button>
		<Button size='lg'>Large</Button>
	</seciton>

</section>
