<script>
	import { penguins } from '$lib/data/penguins.js';
	import { scaleLinear } from 'd3-scale';
	import { extent } from 'd3-array';

	const width = 600;
	const height = 400;

	const xDomain = extent(penguins, (d) => d.bodyMass);
	const yDomain = extent(penguins, (d) => d.flipperLength);

	const xScale = scaleLinear().domain(xDomain).range([0, width]);
	const yScale = scaleLinear().domain(yDomain).range([height, 0]);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	{#each penguins as penguin}
		<circle r="3" fill="red" cx={xScale(penguin.bodyMass)} cy={yScale(penguin.flipperLength)} />
	{/each}
</svg>
