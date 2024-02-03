<script>
	export let number;
	export let penguin;
</script>

<tr>
	<td>#{number}</td>
	<td>{penguin.species}</td>
	<td>{penguin.island}</td>
	<td>{penguin.stage}</td>
</tr>

<style>
	td {
		padding: 0.5em;
		border: 1px solid lightgrey;
	}
</style>
