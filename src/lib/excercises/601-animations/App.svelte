<script>
	import { tweened } from 'svelte/motion';

	const width = 600;
	const height = 400;

	let x = tweened(25);
	let y = tweened(100);

	function move() {
		x.set(Math.random() * width);
		y.set(Math.random() * height);
	}
</script>

<button on:click={move}>Move!</button>
<svg {width} {height} viewBox={`0 0 ${width} ${height}`}>
	<circle cx={$x} cy={$y} r="5" fill="hotpink" />
</svg>
