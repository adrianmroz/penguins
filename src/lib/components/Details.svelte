<script>
	export let header;
</script>

<details>
	<summary>{header}</summary>
	<div>
		<slot />
	</div>
</details>

<style>
	details > summary {
		font-family: Inter, sans-serif;
		background-color: var(--color-primary);
		font-size: var(--size-step-0);
		cursor: pointer;
		padding: 0.5rem 1rem;
	}

	details > summary > * {
		display: inline;
	}

	details > div {
		border: 1px solid var(--color-primary);
		margin-top: 0;
		padding: 1rem;
	}
</style>
