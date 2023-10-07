<script>
	import { tweened } from 'svelte/motion';

	export let x;
	export let y;
	export let color;

	const x$ = tweened(x, { duration: 400 });
	const y$ = tweened(y, { duration: 400 });

	$: {
		x$.set(x);
	}
	$: {
		y$.set(y);
	}
</script>

<circle cx={$x$} cy={$y$} r="4px" fill={color} fill-opacity="0.3" stroke={color} stroke-width="1" />
