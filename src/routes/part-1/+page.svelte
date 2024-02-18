<script>
	import Chart from '$lib/excercises/401-d3-and-svelte/App.svelte';
</script>

<h2 class="uppercase">Bill ratios of Brush-Tailed Penguins</h2>
<p class="lede">Distribution of bill ratios, estimated as bill length divided by bill depth</p>

<div class="bleed">
	<div class="chart">
		<img class="penguins" src="/penguins.png" alt="Penguins" />
		<Chart />
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
