<script>
	import Labels from './Labels.svelte';
	import Axis from './Axis.svelte';
	import Rainclouds from './Rainclouds.svelte';
	import { penguins } from '../data/penguins.js';
	import { scaleBand, scaleLinear, scaleOrdinal } from 'd3-scale';
	import { extent, group } from 'd3-array';

	export let metric;
	export let height = 600;
	export let width = 1200;

	const simplify = (map) => Object.fromEntries(map.entries());

	const labelWidth = 110;
	const axisHeight = 25;
	const rightMargin = 10;
	$: innerHeight = height - axisHeight;
	$: innerWidth = width - labelWidth - rightMargin;
	const colors = ['rgb(255, 110, 1)', 'rgb(199, 92, 203)', 'rgb(9, 112, 117)'];

	const bySpecies = simplify(group(penguins, (d) => d.species));
	const species = Object.keys(bySpecies);

	$: speciesScale = scaleBand().domain(species).range([innerHeight, 0]);
	const colorScale = scaleOrdinal().domain(species.slice().sort()).range(colors);
	const getColor = (d) => d.species;

	function getMetric(metric) {
		switch (metric) {
			case 'billRatio':
				return (d) => d.culmenLength / d.culmenDepth;
			case 'weight':
				return (d) => d.bodyMass;
			case 'flipperLength':
				return (d) => d.flipperLength;
			case 'culmenLength':
				return (d) => d.culmenLength;
			case 'culmenDepth':
				return (d) => d.culmenDepth;
		}
	}

	$: getX = getMetric(metric);
	$: xs = extent(penguins, getX);
	$: xScale = scaleLinear().domain(xs).nice().range([0, innerWidth]);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<g class="labels" transform={'translate(0,0)'}>
		<Labels width={labelWidth} data={species} scale={speciesScale} colors={colorScale} />
	</g>

	<g class="charts" transform={`translate(${labelWidth}, 0)`}>
		<Rainclouds {getX} data={bySpecies} {getColor} {colorScale} yScale={speciesScale} {xScale} />
	</g>

	<g class="axis" transform={`translate(${labelWidth},${innerHeight})`}>
		<Axis scale={xScale} />
	</g>
</svg>
