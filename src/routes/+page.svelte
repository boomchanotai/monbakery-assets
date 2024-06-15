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
