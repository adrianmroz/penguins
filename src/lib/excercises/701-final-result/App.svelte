<script>
	import Chart from '$lib/components/rainclouds/Chart.svelte';

	let width = 600;
	let height = 400;
	let metric = 'billRatio';
</script>

<main>
	<article>
		<select bind:value={metric}>
			<option value="billRatio">Bill Ratios</option>
			<option value="culmenLength">Bill Lengths</option>
			<option value="culmenDepth">Bill Depths</option>
			<option value="weight">Weights</option>
			<option value="flipperLength">Wing lengths</option>
		</select>
		<Chart {metric} {height} {width} />
	</article>
</main>
