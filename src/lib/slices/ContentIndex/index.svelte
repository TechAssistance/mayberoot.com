<script lang="ts">
	import Bounded from '$lib/components/Bounded.svelte';
	import Heading from '$lib/components/Heading.svelte';
	import { isFilled, type Content } from '@prismicio/client';
	import { PrismicRichText } from '@prismicio/svelte';
	import ContentList from './ContentList.svelte';

	export let slice: Content.BlogsSlice;
	export let items: Content.BlogDocument[] | Content.ProjectDocument[];
</script>

<Bounded data-slice-type={slice.slice_type} data-slice-variation={slice.variation}>
	<Heading size="xl" class="mb-8">
		{slice.primary.heading}
	</Heading>
	{#if isFilled.richText(slice.primary.body)}
		<div class="prose prose-xl prose-invert mb-10">
			<PrismicRichText field={slice.primary.body} />
		</div>
	{/if}

	<ContentList {items} viewMoreText={slice.primary.view_more_text} />
</Bounded>
