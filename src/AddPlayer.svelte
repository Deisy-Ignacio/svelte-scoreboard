<script>
	import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    let player ={
        name:'', 
        points:0
    }

    const onSubmit=(e)=>{
        e.preventDefault();
        dispatch('addplayer',player)
    }
</script>

<form on:submit={onSubmit} class="grid-3">
    <input type='text' placeholder="Player Name" bind:value={player.name} />
    <input type='number' placeholder="Player Points" bind:value={player.points} />
    <input type='submit' class='btn btn-primary' placeholder="Player Points" value='add Player'/>
</form>