<script>
	import { lineData } from '$lib/data/line.js';
	import { extent } from 'd3-array';
	import { scaleLinear } from 'd3-scale';
	import { line } from 'd3-shape';

	const width = 600;
	const height = 400;

	const xDomain = extent(lineData, (d) => d.x);
	const yDomain = extent(lineData, (d) => d.y);

	const xScale = scaleLinear().domain(xDomain).range([0, width]);
	const yScale = scaleLinear().domain(yDomain).range([height, 0]);

	const lineFn = line()
		.x((d) => xScale(d.x))
		.y((d) => yScale(d.y));

	const d = lineFn(lineData);

	console.log(d, xDomain, yDomain);
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<path {d} stroke="red" stroke-width="1" fill="none" />
</svg>
