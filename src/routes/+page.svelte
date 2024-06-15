<script>
	import Card from '../components/Card.svelte';
	import Container from '../components/Container.svelte';
	import { data } from '../data';

	const numberOfPage = Math.ceil(data.length / 9);
	let page = 0;
</script>

{#each Array(numberOfPage) as _, i}
	<Container>
		{#each data.slice(i * 9, i * 9 + 9) as item}
			<Card
				text={item.title}
				alternativeText={item.secondTitle}
				price={item.price}
				size={item.size}
			/>
		{/each}
	</Container>
{/each}
<div class="no-print">
	<div class="p-8 space-x-4">
		<button
			type="button"
			on:click={() => {
				window.print();
			}}
			class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
		>
			Print
		</button>

		<a href="/มนเบเกอรี่color.ai.ps">
			<button
				type="button"
				class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
			>
				Download Logo
			</button>
		</a>
	</div>
</div>
