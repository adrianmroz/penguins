<script>
	import { group } from 'd3-array';
	import { penguins } from '$lib/data/penguins.js';
	import { scaleBand } from 'd3-scale';
	import { simplify } from '$lib/utils/simplify.js';
	import Labels from './Labels.svelte';
	import Rainclouds from './Rainclouds.svelte';

	const width = 600;
	const height = 400;

	const labelWidth = 110;
	const axisHeight = 25;

	const innerHeight = height - axisHeight;
	const innerWidth = width - labelWidth;

	const bySpecies = simplify(group(penguins, (d) => d.species));
	const species = Object.keys(bySpecies);

	const speciesScale = scaleBand().domain(species).range([innerHeight, 0]);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<g class="labels" transform={'translate(0,0)'}>
		<Labels width={labelWidth} data={species} scale={speciesScale} />
		<rect x="0" y="0" width={labelWidth} height={innerHeight} fill="hotpink" fill-opacity="0.5" />
	</g>

	<g class="charts" transform={`translate(${labelWidth}, 0)`}>
		<Rainclouds yScale={speciesScale} data={bySpecies} {width} />
		<rect
			x="0"
			y="0"
			width={innerWidth}
			height={innerHeight}
			fill="rebeccapurple"
			fill-opacity="0.5"
		/>
	</g>

	<g class="axis" transform={`translate(${labelWidth},${innerHeight})`}>
		<rect x="0" y="0" width={innerWidth} height={axisHeight} fill="salmon" fill-opacity="0.5" />
	</g>
</svg>
