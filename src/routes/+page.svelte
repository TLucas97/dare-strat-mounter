<script lang="ts">
	import Square from '$lib/square.svelte';

	let squares = 5;
	let selectedHeroes = Array(squares).fill(null);

	const heroNames = [
		'antimage',
		'axe',
		'bane',
		'bloodseeker',
		'crystal_maiden',
		'drow_ranger',
		'earthshaker',
		'juggernaut',
		'mirana',
		'morphling',
		'nevermore',
		'phantom_lancer',
		'puck',
		'pudge',
		'razor',
		'sand_king',
		'storm_spirit',
		'sven',
		'tiny',
		'vengefulspirit',
		'windranger',
		'zuus',
		'kunkka',
		'lina',
		'lich',
		'lion',
		'shadow_shaman',
		'slardar',
		'tidehunter',
		'witch_doctor',
		'riki',
		'enigma',
		'tinker',
		'sniper',
		'necrolyte',
		'warlock',
		'beastmaster',
		'queenofpain',
		'venomancer',
		'faceless_void',
		'skeleton_king',
		'death_prophet',
		'phantom_assassin',
		'pugna',
		'templar_assassin',
		'viper',
		'luna',
		'dragon_knight',
		'dazzle',
		'rattletrap',
		'leshrac',
		'furion',
		'life_stealer',
		'dark_seer',
		'clinkz',
		'omniknight',
		'enchantress',
		'huskar',
		'night_stalker',
		'broodmother',
		'bounty_hunter',
		'weaver',
		'jakiro',
		'batrider',
		'chen',
		'spectre',
		'ancient_apparition',
		'doom_bringer',
		'ursa',
		'spirit_breaker',
		'gyrocopter',
		'alchemist',
		'invoker',
		'silencer',
		'obsidian_destroyer',
		'lycan',
		'brewmaster',
		'shadow_demon',
		'lone_druid',
		'chaos_knight',
		'meepo',
		'treant',
		'ogre_magi',
		'undying',
		'rubick',
		'disruptor',
		'nyx_assassin',
		'naga_siren',
		'keeper_of_the_light',
		'wisp',
		'visage',
		'slark',
		'medusa',
		'troll_warlord',
		'centaur',
		'magnataur',
		'shredder',
		'bristleback',
		'tusk',
		'skywrath_mage',
		'abaddon',
		'elder_titan',
		'legion_commander',
		'techies',
		'ember_spirit',
		'earth_spirit',
		'abyssal_underlord',
		'terrorblade',
		'phoenix',
		'oracle',
		'winter_wyvern',
		'arc_warden',
		'monkey_king',
		'dark_willow',
		'pangolier',
		'grimstroke',
		'void_spirit',
		'snapfire',
		'mars',
		'dawnbreaker'
	];

	const heroes = heroNames.map((name) => ({
		name,
		image: `https://cdn.cloudflare.steamstatic.com/apps/dota2/images/dota_react/heroes/${name}.png`
	}));

	function addSquares() {
		squares += 5;
		selectedHeroes = [...selectedHeroes, ...Array(5).fill(null)];
	}
</script>

<div class="h-screen flex items-center justify-center bg-gray-700 text-white overflow-y-auto">
	<div class="absolute text-white top-0 left-0 m-2 text-xl font-bold">
		<div class="flex gap-2 items-center">
			<img
				src="https://img.icons8.com/?size=256&id=QHArZNJyNSQT&format=png"
				alt="asd"
				class="w-10"
			/>
			Dare+4Dares strat mounter
		</div>
	</div>
	<div class="grid grid-cols-5 gap-4 p-4">
		{#each Array(squares) as _, i}
			<Square {heroes} bind:selected={selectedHeroes[i]} />
		{/each}
	</div>
	<button class="bg-red-700 text-white px-4 py-2 mt-4 text-2xl" on:click={addSquares}>+</button>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Radiance&display=swap');

	* {
		font-family: 'Radiance', sans-serif;
	}
</style>
