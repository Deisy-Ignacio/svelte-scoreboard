<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
	export let name;
	export let points;
	let showControls = false;

	const addPoint=()=> (points +=1);
	const removePoint=()=>(points-=1);
	const toggleControls =()=>(showControls = !showControls);

    const removePlayer=()=>{
        dispatch('removeplayer', name);
    }

</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: rgb(69, 145, 148);
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

	<div class="card">		
		<h1>
			{name}
			<button class="btn btn-sm" on:click={toggleControls}>
				{#if showControls}- {:else}+{/if}
			</button>
            <button class="btn btn-danger" on:click={removePlayer} >remove player</button>
		</h1>
		<h3>{points}</h3>
		{#if showControls}
			<button class="btn" on:click={addPoint}>+1</button>
			<button class="btn btn-dark" on:click={removePoint}>-1</button>
			<input type="number" bind:value={points}>
		{/if}

	</div>