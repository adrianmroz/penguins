<script>
	import Chart from '$lib/excercises/602-animated-rainclouds/Chart.svelte';
	import Select from '$lib/components/Select.svelte';

	let metric = 'billRatio';
</script>

<h2 class="uppercase">
	<Select bind:selected={metric} />
	of Brush-Tailed Penguins
</h2>

<div class="bleed">
	<div class="chart">
		<img class="penguins" src="/penguins.png" alt="Penguins" />
		<Chart {metric} />
	</div>
</div>

<p>
	Gorman, Williams & Fraser (2014) PLoS ONE DOI: 10.1371/journal.pone.0090081 Visualization: Cedric
	Scherer, Illustration: Allison Horst
</p>

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
