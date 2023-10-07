<script>
	import { tweened } from 'svelte/motion';
	import { interpolatePath } from 'd3-interpolate-path';

	export let d;
	export let fill;
	export let stroke;

	const d$ = tweened(d, { duration: 400, interpolate: interpolatePath });

	$: {
		d$.set(d);
	}
</script>

<path {fill} fill-opacity="0.3" {stroke} stroke-width="1" d={$d$} />
