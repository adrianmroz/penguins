<script>
	import Point from './Point.svelte';
	export let data;
	export let getX;
	export let getY;
	export let xScale;
	export let yScale;
	export let colorScale;
	export let getColor;
</script>

{#each data as datum}
	<Point x={xScale(getX(datum))} y={yScale(getY(datum))} color={colorScale(getColor(datum))} />
{/each}
