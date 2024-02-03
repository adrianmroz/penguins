<script>
	import Chart from '$lib/components/rainclouds/Chart.svelte';
	import Select from '$lib/components/Select.svelte';

	let width = 820;
	let height = 400;
	let metric = 'billRatio';
</script>

<main>
	<article>
		<h2 class="uppercase">
			<Select bind:selected={metric} />
			of Brush-Tailed Penguins
		</h2>
		<p class="lede">Distribution of bill ratios, estimated as bill length divided by bill depth</p>
	</article>

	<div class="bleed">
		<div class="chart">
			<img class="penguins" src="/penguins.png" alt="Penguins" />
			<Chart {metric} {height} {width} />
		</div>
	</div>

	<article>
		<p>
			Gorman, Williams & Fraser (2014) PLoS ONE DOI: 10.1371/journal.pone.0090081 Visualization:
			Cedric Scherer, Illustration: Allison Horst
		</p>
	</article>

	<style>
		.uppercase {
			text-transform: uppercase;
		}
		.chart {
			position: relative;
			max-width: 820px;
			margin-inline: auto;
		}
		.penguins {
			position: absolute;
			top: -35px;
			right: 0;
			width: 25%;
		}
	</style>
</main>
