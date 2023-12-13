<script lang="ts">
	export let heroes: any = [];
	export let selected: any = null;
	export let hero_pool = false;

	$: image = selected ? selected.image : '';
</script>

<div class="bg-gray-800 p-4 rounded-lg flex flex-col items-center">
	<select class="w-full bg-gray-700 text-white p-2 rounded" bind:value={selected}>
		<option value={null} disabled selected>Select a hero</option>
		{#each heroes as hero}
			<option value={hero}>{hero.name}</option>
		{/each}
	</select>
	{#if selected}
		<img src={image} alt={selected.name} class="w-16 h-16 rounded-full mt-5" />
		{#if hero_pool}
			<input type="text" placeholder="Player" class="p-2 bg-gray-700 border mt-2" />
		{/if}
	{/if}
</div>
