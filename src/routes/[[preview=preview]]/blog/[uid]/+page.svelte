<script>
	import { SliceZone } from '@prismicio/svelte';

	import { components } from '$lib/slices';
	import Bounded from '$lib/components/Bounded.svelte';
    import ContentBody from '$lib/components/ContentBody.svelte';

	export let data;
</script>

<ContentBody page={data.page} />
