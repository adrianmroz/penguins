<script>
	import { area, curveBasis } from 'd3-shape';

	export let xScale;
	export let yScale;
	export let data;
	export let getX;
	export let getY;
	export let color;

	$: areaFn = area()
		.curve(curveBasis)
		.x((d) => xScale(getX(d)))
		.y0(yScale(0))
		.y1((d) => yScale(getY(d)));

	$: d = areaFn(data);
</script>

<path fill={color} fill-opacity="0.3" stroke={color} stroke-width="1" {d} />
