<script lang="ts">
	import { base } from '$app/paths';
	import type { Course } from '$lib/teachings';
	import Line from './Line.svelte';

	export let data: {
		courses: Course[];
	};
</script>

<svelte:head>
	<title>CSUnibo | Homepage</title>
	<!-- OG meta graph -->
	<meta name="title" property="og:title" content="Risorse CSUnibo" />
	<meta name="type" property="og:type" content="website" />
	<meta name="description" property="og:description" content="Risorse per gli studenti dei corsi di laurea del dipartimento di informatica (DISI) dell'Università di Bologna"/>
</svelte:head>

<div class="flex justify-center">
	<div class="container max-w-5xl">
		<div class="m-10">
			<h1 class="text-4xl font-semibold text-center">Risorse</h1>
			<h3 class="text-2 font-semibold text-center">Raccolte di materiali per lo studio da CSUnibo</h3>
		</div>
		<ul class="menu p-2 text-lg">
			{#each data.courses as course}
				<Line name={course.name} icon={course.icon} href="{base}/dash/{course.id}" />
			{/each}

			<Line name="Settings" icon="🔧" href="{base}/settings" />
		</ul>
	</div>
</div>
