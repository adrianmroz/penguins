<script>
	let count = 0;

	function increment() {
		count = count + 1;
	}
</script>

<main>
	<article>
		<div>Count: {count}</div>
		<button on:click={increment}>Increment</button>
	</article>
</main>
