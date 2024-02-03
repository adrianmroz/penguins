<script>
	import Repl from '$lib/components/Repl.svelte';
	import Details from './Details.svelte';

	export let id;
</script>

<Details header="Show solution">
	<Repl {id}>Edit solution in Svelte REPL</Repl>
</Details>
