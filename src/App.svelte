<script>
	import Navbar from "./Navbar.svelte";
	import Player from "./Player.svelte";
	import AddPlayer from "./AddPlayer.svelte";

	let players = [
		{
			name: "Matrix",
			point: 100
		},
		{
			name: "Virus",
			point: 10
		},
		{
			name: "Smith",
			point: 30
		}
	];

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	};


	const removePlayer = (e) => {
		players = players.filter(player => player.name !== e.detail);
	};
</script>

<Navbar />
<AddPlayer on:addplayer = {addPlayer} />
<main>
	{#if players.length === 0} <p>No Players</p>
	{:else}
	{#each players as player}
		<Player name = {player.name} point = {player.point} on:removeplayer = {removePlayer} />
	{/each}
	{/if}
</main>

<style>
	main {
		display: flex;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.contain{
		width: 50%;
		text-align: center;
	}
	.primary{
		color: #bbb;
	}
</style>