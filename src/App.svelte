<script>
	import Navbar from "./Navbar.svelte";
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players =[
		{
			name: 'Deisy',
			points: 100
		},
		{
			name: 'Ana',
			points: 800
		},
		{
			name: 'Saúl',
			points: 85
		},
		{
			name: 'Joshua',
			points: 85
		}
	]

	const addPlayer=(e)=>{
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	}

	const removePlayer=(e)=>{
		players = players.filter(player=>player.name!==e.detail);
	}
</script>


<Navbar/>
<div class="container">
	<AddPlayer on:addplayer={addPlayer}/>
	{#if players.lenght ===0 }
		<h1>No Players</h1>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} on:removeplayer={removePlayer}/>
		{/each}
	{/if}	
</div>