<script>
	import { penguins } from '$lib/data/penguins.js';
	import Row from './Row.svelte';
</script>

<table>
	<thead>
		<tr>
			<th>Number</th>
			<th>Species</th>
			<th>Island</th>
			<th>Stage</th>
		</tr>
	</thead>
	<tbody>
		{#each penguins as penguin, i}
			<Row {penguin} number={i} />
		{/each}
	</tbody>
</table>

<style>
	:global(table) {
		color: #333;
		background: white;
		border: 1px solid grey;
		font-size: 12pt;
		border-collapse: collapse;
	}

	:global(table thead th, table tfoot th) {
		color: #777;
		background: rgba(0, 0, 0, 0.1);
	}
	:global(table th, table td) {
		padding: 0.5em;
		border: 1px solid lightgrey;
	}
</style>
