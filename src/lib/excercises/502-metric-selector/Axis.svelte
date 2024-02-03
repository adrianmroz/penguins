<script>
	import { axisBottom } from 'd3-axis';
	import { select } from 'd3-selection';

	export let scale;

	let axisGroup;
	$: {
		if (axisGroup) {
			let axisSelection = select(axisGroup);
			let axisFn = axisBottom(scale);
			axisSelection.call(axisFn);
		}
	}
</script>

<g class="axis" bind:this={axisGroup} transform="translate(0,8)" />

<style>
	.axis {
		color: rgb(128, 128, 128);
	}
</style>
