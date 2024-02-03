<script>
	import { penguins } from '$lib/data/penguins.js';
	import { scaleLinear, scaleOrdinal } from 'd3-scale';
	import { extent } from 'd3-array';
	import Point from './Point.svelte';

	const width = 600;
	const height = 400;

	const xDomain = extent(penguins, (d) => d.bodyMass);
	const yDomain = extent(penguins, (d) => d.flipperLength);

	const xScale = scaleLinear().domain(xDomain).range([0, width]);
	const yScale = scaleLinear().domain(yDomain).range([height, 0]);

	const colorScale = scaleOrdinal()
		.domain(['Adelie', 'Gentoo', 'Chinstrap'])
		.range(['rgb(255, 110, 1)', 'rgb(199, 92, 203)', 'rgb(9, 112, 117)']);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	{#each penguins as penguin}
		<Point
			x={xScale(penguin.bodyMass)}
			y={yScale(penguin.flipperLength)}
			color={colorScale(penguin.species)}
		/>
	{/each}
</svg>
