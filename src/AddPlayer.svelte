<script>
	import { createEventDispatcher } from 'svelte';

	const dispatcher = createEventDispatcher();

	let player = {
		name: "",
		point: 0
	}

	const submit = (e) => {
			e.preventDefault();
			dispatcher("addplayer", player);
			player = {
				name: "",
				point: 0
			}
		}
</script>

<div class="contain">
	<form on:submit = {submit}>
		<input type="text" name="" placeholder="Name" bind:value={player.name}>
		<input type="number" name="" placeholder="Point" bind:value={player.point}>
		<button class="primary" type="submit">Add Player</button>
	</form>
</div>

<style>
	.contain{
		padding: 10px;
		display: block;
		text-align: center;
	}
</style>