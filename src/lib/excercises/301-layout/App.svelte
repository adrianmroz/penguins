<script>
	const width = 600;
	const height = 400;

	const labelWidth = 110;
	const axisHeight = 25;

	const innerHeight = height - axisHeight;
	const innerWidth = width - labelWidth;
</script>

<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<g class="labels" transform={'translate(0,0)'}>
		<rect x="0" y="0" width={labelWidth} height={innerHeight} fill="hotpink" fill-opacity="0.5" />
	</g>

	<g class="charts" transform={`translate(${labelWidth}, 0)`}>
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
