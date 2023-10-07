<script>
	import { penguins } from '$lib/data/penguins.js';
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
			<tr>
				<td>{i}</td>
				<td>{penguin.species}</td>
				<td>{penguin.island}</td>
				<td>{penguin.stage}</td>
			</tr>
		{/each}
	</tbody>
</table>

<style>
	table {
		color: #333;
		background: white;
		border: 1px solid grey;
		font-size: 12pt;
		border-collapse: collapse;
	}
	table thead th,
	table tfoot th {
		color: #777;
		background: rgba(0, 0, 0, 0.1);
	}
	table th,
	table td {
		padding: 0.5em;
		border: 1px solid lightgrey;
	}
</style>
