<script lang="ts">
	import '../app.pcss';
	import { global_store } from '$lib/global';
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';

	function clearHeroFields() {
		if (typeof window !== 'undefined') {
			if ($page.url.pathname === '/') {
				$global_store.hero_fields = [
					{
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
							},
							{
								name: ''
							}
						]
					}
				];
				localStorage.setItem('hero_fields', JSON.stringify($global_store.hero_fields));
			} else {
				$global_store.hero_pool_fields = [
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
	}

	onMount(() => {
		if (typeof window !== 'undefined') {
			if (localStorage.getItem('hero_fields')) {
				$global_store.hero_fields = JSON.parse(localStorage.getItem('hero_fields') as string);
			}
			if (localStorage.getItem('hero_pool_fields')) {
				$global_store.hero_pool_fields = JSON.parse(
					localStorage.getItem('hero_pool_fields') as string
				);
			}
		}
	});
</script>

<main class="h-screen w-full flex items-center justify-center bg-gray-900">
	<div class="bg-gray-800 rounded-lg h-[700px] w-[1100px] text-white p-5 overflow-y-auto">
		<div class="flex justify-between">
			<div class="flex gap-2">
				<button
					class="bg-gray-700 px-3 py-2 font-bold text-sm flex items-center gap-2 hover:opacity-70 border border-gray-700"
					class:!border-white={$page.url.pathname === '/'}
					on:click={() => goto('/')}
				>
					HERO STRATS
				</button>
				<button
					class="bg-gray-700 px-3 py-2 font-bold text-sm flex items-center gap-2 hover:opacity-70 border border-gray-700"
					class:!border-white={$page.url.pathname === '/heropool'}
					on:click={() => goto('/heropool')}
				>
					HERO POOL
				</button>
			</div>
			<button
				class="bg-red-500 px-3 py-2 font-bold text-sm flex items-center gap-2 hover:opacity-70"
				on:click={clearHeroFields}
			>
				CLEAR FIELDS
			</button>
		</div>
		<div class="mt-5">
			<slot />
		</div>
	</div>
</main>
