<script>
	import { spring } from 'svelte/motion';

	let count = 0;

	const displayed_count = spring();
	$: displayed_count.set(count);
	$: offset = modulo($displayed_count, 1);

	function modulo(n, m) {
		// handle negative numbers
		return ((n % m) + m) % m;
	}
</script>

<section>
	<div class="flex border-y mt-4">
		<button on:click={() => (count -= 1)} aria-label="Decrease the counter by one" class="btn">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5" />
			</svg>
		</button>

		<div class="counter-viewport">
			<div class="counter-digits" style="transform: translate(0, {100 * offset}%)">
				<strong class="hidden" aria-hidden="true">{Math.floor($displayed_count + 1)}</strong>
				<strong>{Math.floor($displayed_count)}</strong>
			</div>
		</div>

		<button on:click={() => (count += 1)} aria-label="Increase the counter by one" class="btn">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
			</svg>
		</button>
	</div>
	<button class="btn !w-full p-3" on:click={() => (count = 0)} aria-label="Reset counter to zero">
		Reset
	</button>
</section>

<style lang="postcss">
	.btn {
		@apply flex flex-col items-center justify-center w-16 hover:bg-slate-300 text-3xl;
	}
	svg {
		width: 25%;
		height: 25%;
	}
	path {
		vector-effect: non-scaling-stroke;
		stroke-width: 2px;
		stroke: #444;
	}

	.counter-viewport {
		width: 8em;
		height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
	}

	.counter-viewport strong {
		position: absolute;
		display: flex;
		width: 100%;
		height: 100%;
		font-weight: 400;
		color: var(--color-theme-1);
		font-size: 4rem;
		align-items: center;
		justify-content: center;
	}

	.counter-digits {
		position: absolute;
		width: 100%;
		height: 100%;
	}

	.hidden {
		top: -100%;
		user-select: none;
	}
</style>
