<script>
	import Chart from './Chart.svelte';
	import Select from './Select.svelte';

	let width = 1200;
	let height = 600;
	let metric = 'billRatio';
</script>

<main>
	<div class="header">
		<div class="title">
			<Select bind:selected={metric} />
			of Brush-Tailed Penguins (<span class="italic">Pygoscelis</span> spec.)
		</div>
		<div class="subtitle">
			Distribution of bill ratios, estimated as bill length divided by bill depth
		</div>
	</div>

	<div class="chart">
		<img class="penguins" src="/penguins.png" alt="Penguins" />
		<div class="container" bind:clientWidth={width} bind:clientHeight={height}>
			<Chart {metric} {height} {width} />
		</div>
	</div>
	<div class="footer">
		<div>Gorman, Williams & Fraser (2014) PLoS ONE DOI: 10.1371/journal.pone.0090081</div>
		<div>Visualization: Cedric Scherer, Illustration: Allison Horst</div>
	</div>
</main>

<style>
	main {
		display: flex;
		height: 100vh;
		flex-direction: column;
		font-family: Source Code Pro, Consolas, Andale Mono WT, Andale Mono, Lucida Console,
			Lucida Sans Typewriter, DejaVu Sans Mono, Bitstream Vera Sans Mono, Liberation Mono,
			Nimbus Mono L, Monaco, Courier New, Courier, monospace;
	}

	.header {
		padding: 1rem 2rem;
	}

	.title {
		font-weight: 600;
		font-size: 1.5rem;
		line-height: 2rem;
	}

	.subtitle {
		font-style: italic;
		font-weight: 300;
		font-size: 1rem;
		line-height: 1.5rem;
	}

	.chart {
		flex: 1 1 auto;
		position: relative;
	}

	.container {
		position: absolute;
		top: 0;
		left: 10px;
		right: 30px;
		bottom: 0;
	}

	.footer {
		text-align: end;
		font-weight: 300;
		font-size: 1rem;
		line-height: 1.5rem;
		padding-right: 1rem;
		padding-bottom: 0.5rem;
	}

	.penguins {
		position: absolute;
		top: -35px;
		right: 0;
		width: 25%;
	}
</style>
