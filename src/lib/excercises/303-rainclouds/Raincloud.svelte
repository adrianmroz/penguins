<script>
	import { scaleLinear } from 'd3-scale';
	import Scatterplot from './Scatterplot.svelte';

	export let data;
	export let getColor;
	export let colorScale;
	export let getX;
	export let xScale;
	export let height;

	const rainRatio = 0.3;
	const cloudHeight = height * (1 - rainRatio);
	const rainHeight = height * rainRatio;

	const yScale = scaleLinear()
		.domain([0, 1])
		.range([rainHeight - 10, 10]);

	const getY = () => Math.random();
</script>

<g class="cloud" />

<g class="rain" transform={`translate(0, ${cloudHeight})`}>
	<Scatterplot {data} {getX} {xScale} {getY} {yScale} {getColor} {colorScale} />
</g>
