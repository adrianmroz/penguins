<script>
	import Scatterplot from './Scatterplot.svelte';
	import Histogram from './Histogram.svelte';
	import { scaleLinear } from 'd3-scale';

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

<g class="cloud">
	<!--	<rect x="0" y="0" {width} height={height / 2} fill={color} fill-opacity="0.2" />-->
	<Histogram {xScale} {data} {getX} {colorScale} {getColor} height={cloudHeight} />
</g>

<g class="rain" transform={`translate(0, ${cloudHeight})`}>
	<!--	<rect-->
	<!--		x="0"-->
	<!--		y="0"-->
	<!--		{width}-->
	<!--		height={height / 2}-->
	<!--		fill={colorScale(getColor(data[0]))}-->
	<!--		fill-opacity="0.7"-->
	<!--	/>-->
	<Scatterplot {data} {getX} {xScale} {getY} {yScale} {getColor} {colorScale} />
</g>
