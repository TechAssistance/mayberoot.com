<script>
	import { SliceZone } from '@prismicio/svelte';

	import { components } from '$lib/slices';
	import Bounded from '$lib/components/Bounded.svelte';

	export let data;
</script>



<Bounded tag="article">
    <div class="rounded-2xl">
        
    </div>
</Bounded>

<SliceZone slices={data.page.data.slices} {components} />
