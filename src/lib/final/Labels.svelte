<script>
	export let data;
	export let scale;
	export let colors;
	export let width;
</script>

{#each data as datum}
	<g transform={`translate(0, ${scale(datum)})`}>
		<text x={width - 10} text-anchor="end" y={scale.bandwidth() / 2} fill={colors(datum)}
			>{datum}</text
		>
	</g>
{/each}
