<script lang="ts">
	import type { Teaching, TeachingYear } from '$lib/teachings';
	import { base } from '$app/paths';

	export let years: TeachingYear[];
	export let activeYears: Teaching[];
	export let title: string;
</script>

<ul class="menu p-2">
	{#each years as year}
		{#if year.teachings.length > 0}
			<li class="menu-title">
				<span class="text-2xl mt-5 italic">{year.year} anno {title}</span>
			</li>
			<div class="divider mt-0"></div>
			<div class="flex flex-row flex-wrap">
				{#each year.teachings as teaching}
					{@const disabled = !activeYears.includes(teaching)}
					{@const href = base + '/' + teaching.url}
					<a href={disabled ? null : href} class="text-center text-lg">
						<li
							class:disabled
							class="flex flex-row xs:flex-1 justify-center border-base-content items-center m-2 border-2 rounded-md join"
						>
							<a href={disabled ? null : href} class="text-center text-lg join-item">
								{teaching.name ? teaching.name : teaching.url}
							</a>
							{#if teaching.telegram != null && teaching.telegram !== ''}
								<a
									href="https://t.me/{teaching.telegram}"
									class="text-center text-lg join-item border-l-2">👥</a
								>
							{/if}
						</li>
					</a>
				{/each}
			</div>
		{/if}
	{/each}
</ul>
