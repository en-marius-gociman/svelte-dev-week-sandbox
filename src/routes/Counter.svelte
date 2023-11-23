<script lang="ts">
	import {onMount} from 'svelte';
	import { countVal } from '../store/counterStore.ts';

	export let initialValue;

	const addOne = () => {
		countVal.update((prevVal) => prevVal+=1)
	}

	const subtractOne = () => {
		 countVal.update((prevVal) => prevVal >= 1 ? prevVal-=1 : prevVal)
	}

	const reset = () => {
		initialValue >= 0 ? countVal.set(initialValue) : countVal.set(0)
	}

	onMount(() => {
		initialValue >= 0 && countVal.set(initialValue)
	});

</script>

<div class="counter">
	<button on:click={subtractOne} aria-label="Decrease the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5" />
		</svg>
	</button>

	<button on:click={reset} aria-label="Reset the counter">
		<h6>Reset</h6>
	</button>

	<button on:click={addOne} aria-label="Increase the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
		</svg>
	</button>

	
</div>

<style>
	.counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}

	.counter button {
		width: 2em;
		height: 1em;
		padding: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 0;
		background-color: transparent;
		touch-action: manipulation;
		font-size: 2rem;
	}

	.counter button:hover {
		background-color: var(--color-bg-1);
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

</style>
