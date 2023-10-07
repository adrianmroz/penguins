<script>
	export let selected;
</script>

<span class="custom-select">
	<select bind:value={selected}>
		<option value="billRatio">Bill Ratios</option>
		<option value="culmenLength">Bill Lengths</option>
		<option value="culmenDepth">Bill Depths</option>
		<option value="weight">Weights</option>
		<option value="flipperLength">Wing lengths</option>
	</select>
</span>

<style>
	select {
		appearance: none;
		/* safari */
		-webkit-appearance: none;
		/* other styles for aesthetics */
		padding-left: 0.5rem;
		padding-right: 2rem;
		background-color: #fff;
		border: 0;
		text-transform: inherit;
		box-sizing: content-box;
		cursor: pointer;
		font-weight: inherit;
		font-size: inherit;
		line-height: inherit;
	}

	.custom-select {
		position: relative;
	}

	.custom-select::after {
		position: absolute;
		content: '';
		right: 0.5rem;
		pointer-events: none;
	}

	.custom-select::after {
		border-left: 0.4rem solid transparent;
		border-right: 0.4rem solid transparent;
		border-top: 0.5rem solid var(--color-primary);
		top: 40%;
	}

	.custom-select::before {
		position: absolute;
		top: 85%;
		content: ' ';
		border-bottom: 4px solid var(--color-primary);
		width: 100%;
	}
</style>
