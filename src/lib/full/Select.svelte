<script>
	export let selected;
</script>

<span class="custom-select">
	<select bind:value={selected}>
		<option value="billRatio">Bill Ratios</option>
		<option value="culmenLength">Bill Lengths</option>
		<option value="culmenDepth">Bill Depths</option>
		<option value="weight">Weights</option>
		<option value="flipperLength">Flipper Lengths</option>
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
		border-bottom: 2px solid black;
		color: #000;
		cursor: pointer;
		font-weight: 600;
		font-size: 1.5rem;
		line-height: 2rem;
		font-family: Source Code Pro, Consolas, Andale Mono WT, Andale Mono, Lucida Console,
			Lucida Sans Typewriter, DejaVu Sans Mono, Bitstream Vera Sans Mono, Liberation Mono,
			Nimbus Mono L, Monaco, Courier New, Courier, monospace;
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
		border-top: 0.5rem solid black;
		top: 40%;
	}
</style>
