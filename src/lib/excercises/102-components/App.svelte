<script>
	import { penguins } from '$lib/data/penguins.js';
	import { scaleLinear, scaleOrdinal } from 'd3-scale';
	import { extent } from 'd3-array';
	import Scatterplot from './Scatterplot.svelte';

	const width = 600;
	const height = 400;

	const getX = (d) => d.bodyMass;
	const xDomain = extent(penguins, getX);
	const getY = (d) => d.flipperLength;
	const yDomain = extent(penguins, getY);

	const xScale = scaleLinear().domain(xDomain).range([0, width]);
	const yScale = scaleLinear().domain(yDomain).range([height, 0]);

	const getColor = (d) => d.species;
	const colorScale = scaleOrdinal()
		.domain(['Adelie', 'Gentoo', 'Chinstrap'])
		.range(['rgb(255, 110, 1)', 'rgb(199, 92, 203)', 'rgb(9, 112, 117)']);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<Scatterplot data={penguins} {getX} {getColor} {getY} {colorScale} {yScale} {xScale} />
</svg>
