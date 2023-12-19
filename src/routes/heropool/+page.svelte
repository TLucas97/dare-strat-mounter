<script lang="ts">
	import { global_store } from '$lib/global';

	const hero_names = [
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
		'dawnbreaker',
		'muerta',
		'primal_beast'
	];

	function increaseHeroFields() {
		if (typeof window !== 'undefined') {
			$global_store.hero_pool_fields = [
				...$global_store.hero_pool_fields,
				{
					player: '',
					hero_squares: [
						{
							name: ''
						},
						{
							name: ''
						},
						{
							name: ''
						},
						{
							name: ''
						}
					]
				}
			];
			localStorage.setItem('hero_pool_fields', JSON.stringify($global_store.hero_pool_fields));
		}
	}
</script>

<div class="flex flex-col gap-8">
	{#each $global_store.hero_pool_fields as field}
		<div class="flex flex-col gap-3">
			<div>
				<input
					type="text"
					class="bg-gray-700 p-2 focus:outline-none"
					placeholder="Insert player name here"
					bind:value={field.player}
				/>
			</div>
			<div class="flex justify-between gap-2">
				{#each field.hero_squares as hero}
					<div class="flex flex-col">
						<select class={`text-black p-2 bg-cover`} bind:value={hero.name}>
							<option value="" selected disabled>Select a hero</option>
							{#each hero_names as heroName}
								<option value={heroName}>{heroName}</option>
							{/each}
						</select>
						<img
							src={`https://cdn.cloudflare.steamstatic.com/apps/dota2/images/dota_react/heroes/${
								hero.name || 'antimage'
							}.png`}
							alt="dota2"
							class="w-full h-[80px] object-cover"
						/>
					</div>
				{/each}
			</div>
		</div>
	{/each}
</div>
<div class="flex items-center justify-center mt-5">
	<button
		class="bg-gray-500 px-3 py-2 font-bold text-sm flex items-center gap-2 hover:opacity-70"
		on:click={increaseHeroFields}
	>
		MORE HERO POOLS <span class="text-2xl">+</span>
	</button>
</div>
