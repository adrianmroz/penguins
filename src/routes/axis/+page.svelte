<script>
	import { extent, group } from 'd3-array';
	import { penguins } from '$lib/data/penguins.js';
	import { scaleBand, scaleLinear, scaleOrdinal } from 'd3-scale';
	import { simplify } from '$lib/utils/simplify.js';
	import Labels from './Labels.svelte';
	import Rainclouds from './Rainclouds.svelte';
	import Axis from './Axis.svelte';

	const width = 600;
	const height = 400;

	const labelWidth = 110;
	const axisHeight = 25;

	const innerHeight = height - axisHeight;
	const innerWidth = width - labelWidth;

	const bySpecies = simplify(group(penguins, (d) => d.species));
	const species = Object.keys(bySpecies);

	const speciesScale = scaleBand().domain(species).range([innerHeight, 0]);

	const colors = ['rgb(255, 110, 1)', 'rgb(199, 92, 203)', 'rgb(9, 112, 117)'];
	const colorScale = scaleOrdinal().domain(species.slice().sort()).range(colors);
	const getColor = (d) => d.species;

	const getX = (d) => d.culmenLength / d.culmenDepth;
	const xs = extent(penguins, getX);
	const xScale = scaleLinear().domain(xs).nice().range([0, innerWidth]);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<g class="labels" transform={'translate(0,0)'}>
		<Labels width={labelWidth} data={species} scale={speciesScale} />
	</g>

	<g class="charts" transform={`translate(${labelWidth}, 0)`}>
		<Rainclouds {getX} data={bySpecies} {getColor} {colorScale} yScale={speciesScale} {xScale} />
	</g>

	<g class="axis" transform={`translate(${labelWidth},${innerHeight})`}>
		<Axis scale={xScale} />
	</g>
</svg>
