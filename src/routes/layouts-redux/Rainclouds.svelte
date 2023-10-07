<script>
	import Raincloud from './Raincloud.svelte';

	export let data;
	export let yScale;
	export let width;
</script>

{#each Object.keys(data) as key}
	<g transform={`translate(0, ${yScale(key)})`}>
		<Raincloud species={key} {width} height={yScale.bandwidth()} />
	</g>
{/each}
