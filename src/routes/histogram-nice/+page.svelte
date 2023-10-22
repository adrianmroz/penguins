<script>
	import { extent } from 'd3-array';
	import { scaleLinear } from 'd3-scale';
	import { penguins } from '$lib/data/penguins.js';
	import Histogram from './Histogram.svelte';

	const width = 600;
	const height = 400;

	const getX = (d) => d.bodyMass;
	const xDomain = extent(penguins, getX);
	const xScale = scaleLinear().domain(xDomain).range([0, width]);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<Histogram
		data={penguins}
		{xScale}
		{height}
		{getX}
		getColor={() => 'rebeccapurple'}
		colorScale={(x) => x}
	/>
</svg>
