<script>

	import { createEventDispatcher } from 'svelte';

	const dispatcher = createEventDispatcher();

	export let name;
	export let point;

	const plus = () => point+=1;
	const remove = () => point-=1;

	let showControls = true;

	const toggleControls = () => showControls = !showControls;

	const Delete = () => dispatcher("removeplayer", name);
</script>

<div class="contain">
	<h1>{name}!</h1>
	<h3>{point}</h3>
	<button on:click = {toggleControls}>Toggle Controls {#if showControls} - {:else} + {/if}</button>
	{#if showControls}
		<button on:click = {plus}>Add point</button>
		<button on:click = {remove}>Remove point</button>
		<button class = "danger" on:click = {Delete}>X</button>
		<input type="number" bind:value={point}>
	{/if}
</div>

<style>
	button{
		padding: 5px;
		background-color: #4f5;
	}
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	.contain{
		text-align: center;
		width: 33%;
	}
	.danger{
		background-color: red;
	}
</style>