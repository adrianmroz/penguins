<script>
	import Raincloud from './Raincloud.svelte';

	export let data;
	export let getColor;
	export let colorScale;
	export let getX;
	export let yScale;
	export let xScale;
</script>

{#each Object.keys(data) as key}
	<g transform={`translate(0, ${yScale(key)})`}>
		<Raincloud
			data={data[key]}
			{getX}
			{xScale}
			height={yScale.bandwidth()}
			{getColor}
			{colorScale}
		/>
	</g>
{/each}
