<script>
	import { max, bin, extent } from 'd3-array';
	import { scaleLinear } from 'd3-scale';
	import { penguins } from '$lib/data/penguins.js';
	import { area, curveBasis } from 'd3-shape';

	const width = 600;
	const height = 400;

	const xDomain = extent(penguins, (d) => d.bodyMass);
	const xScale = scaleLinear().domain(xDomain).range([0, width]);

	const binFn = bin()
		.value((d) => d.bodyMass)
		.thresholds(20);

	const bins = binFn(penguins);

	const yScale = scaleLinear()
		.domain([0, max(bins, (d) => d.length)])
		.range([height, 0]);

	const midpoint = (d) => (d.x0 + d.x1) / 2;
	const count = (d) => d.length;

	const areaFn = area()
		.curve(curveBasis)
		.x((d) => xScale(midpoint(d)))
		.y0(yScale(0))
		.y1((d) => yScale(count(d)));

	const d = areaFn(bins);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<path fill="rebeccapurple" fill-opacity="0.3" stroke="rebeccapurple" stroke-width="1" {d} />
</svg>
