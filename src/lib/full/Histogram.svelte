<script>
	import { max, bin } from 'd3-array';
	import { scaleLinear } from 'd3-scale';
	import HistogramArea from '$lib/full/HistogramArea.svelte';
	export let data;
	export let getX;
	export let xScale;
	export let colorScale;
	export let getColor;
	export let height;

	$: yScale = scaleLinear()
		.domain([0, max(bins, (d) => d.length)])
		.range([height, 0]);

	$: binFn = bin().value(getX).thresholds(20);
	$: bins = binFn(data);

	const midpoint = (d) => (d.x0 + d.x1) / 2;
	const count = (d) => d.length;

	$: color = data.length > 0 ? colorScale(getColor(data[0])) : 'hotpink';
</script>

<HistogramArea data={bins} {xScale} {yScale} {color} getY={count} getX={midpoint} />
