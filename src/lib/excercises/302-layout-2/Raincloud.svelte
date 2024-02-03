<script>
	export let width;
	export let height;

	const rainRatio = 0.3;
	const cloudHeight = height * (1 - rainRatio);
	const rainHeight = height * rainRatio;
</script>

<g class="cloud">
	<rect x="0" y="0" {width} height={cloudHeight} fill="gray" fill-opacity="0.2" />
	<text x="100" y={cloudHeight / 2}>Cloud</text>
</g>

<g class="rain" transform={`translate(0, ${cloudHeight})`}>
	<rect x="0" y="0" {width} height={rainHeight} fill="gray" fill-opacity="0.7" />
	<text x="100" y={rainHeight / 2}>Rain</text>
</g>
