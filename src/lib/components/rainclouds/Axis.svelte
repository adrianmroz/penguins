<script>
	import { axisBottom } from 'd3-axis';
	import { select } from 'd3-selection';
	import 'd3-transition';

	export let scale;

	let axisGroup;
	$: {
		if (axisGroup) {
			let axisSelection = select(axisGroup);
			let axisFn = axisBottom(scale);
			axisSelection.transition().duration(400).call(axisFn);
		}
	}
</script>

<g class="axis" bind:this={axisGroup} transform="translate(0,8)" />

<style>
	.axis {
		color: rgb(128, 128, 128);
	}
</style>
