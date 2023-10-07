<script>
	import AreaChart from './AreaChart.svelte';
	import { bin, max } from 'd3-array';
	import { scaleLinear } from 'd3-scale';

	export let data;
	export let xScale;
	export let getX;
	export let height;
	export let getColor;
	export let colorScale;

	$: binFn = bin().value(getX).thresholds(20);

	$: bins = binFn(data);

	$: yScale = scaleLinear()
		.domain([0, max(bins, (d) => d.length)])
		.range([height, 0]);

	const midpoint = (d) => (d.x0 + d.x1) / 2;
	const count = (d) => d.length;

	$: color = data.length > 0 ? colorScale(getColor(data[0])) : 'currentColor';
</script>

<AreaChart data={bins} {color} {xScale} {yScale} getX={midpoint} getY={count} />
