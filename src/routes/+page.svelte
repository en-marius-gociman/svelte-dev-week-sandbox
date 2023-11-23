<script>
	import Counter from './Counter.svelte';
	import { countVal } from '../store/counterStore.ts'

	let count = 0;
	countVal.subscribe((val) => count = val)

</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		Svelte counter
	</h1>
	<div class="counter-viewport">
			<h1>
				{count}
			</h1>
	</div>
	<Counter initialValue={5}/>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.counter-viewport {
		width: 8em;
		height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
	}
</style>
