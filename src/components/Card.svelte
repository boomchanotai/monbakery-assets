<script>
	export let text;
	export let alternativeText;
	export let price;
	export let size;

	import { tv } from 'tailwind-variants';

	const card = tv({
		slots: {
			base: 'border border-black p-2 flex flex-col items-center justify-center gap-4 font-black',
			title: 'text-4xl text-center leading-normal',
			secondaryTitle: 'text-2xl text-center',
			description: 'text-4xl'
		},
		variants: {
			size: {
				sm: {
					base: 'w-[8cm] h-[5cm]',
					title: text.length > 23 ? 'text-3xl' : 'text-4xl'
				},
				md: {
					base: 'w-[9cm] h-[6cm]',
					title: text.length > 23 ? 'text-3xl' : 'text-4xl'
				},
				lg: {
					base: 'w-[23cm] h-[5cm]'
				}
			}
		},
		defaultVariants: {
			size: 'md'
		}
	});

	const { base, title, secondaryTitle, description } = card({ size });
</script>

<div class={base()}>
	<h2 class={title()}>
		{text}
	</h2>
	{#if alternativeText}
		<p class={secondaryTitle()}>{alternativeText}</p>
	{/if}
	<p class={description()}>{price} บาท</p>
</div>
