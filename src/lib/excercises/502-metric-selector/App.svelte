<script>
	import Chart from './Chart.svelte';

	let metric = 'billRatio';
</script>

<select bind:value={metric}>
	<option value="billRatio">Bill Ratios</option>
	<option value="culmenLength">Bill Lengths</option>
	<option value="culmenDepth">Bill Depths</option>
	<option value="weight">Weights</option>
	<option value="flipperLength">Wing lengths</option>
</select>
<Chart {metric} />
