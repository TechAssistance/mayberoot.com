<script lang="ts">
	import type { Content } from '@prismicio/client';
    import Scene from './Scene.svelte';
	export let slice: Content.HeroSlice;
    import gsap from 'gsap';
	import { onMount } from 'svelte';
    const welcome_letters = slice.primary.welcome?.split("") ?? "";
    const name_letters = slice.primary.name?.split("") ?? "";
    
    onMount(() => {
		const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
		if (prefersReducedMotion) {
			gsap.to('.name-animation', { opacity: 1 });
			gsap.to('.job-title', { opacity: 1 });
			return;
		}

		const tl = gsap.timeline();

		tl.fromTo(
			'.name-animation',
			{
				x: -100,
				opacity: 0,
				rotate: -10
			},
			{
				x: 0,
				rotate: 0,
				opacity: 1,
				ease: 'elastic.out(1,0.3)',
				duration: 1,
				transformOrigin: 'left top',
				delay: 0.2,
				stagger: {
					each: 0.1,
					from: 'random'
				}
			}
		);

		tl.fromTo(
			'.job-title',
			{
				y: 20,
				opacity: 0,
				scale: 1.2
			},
			{
				opacity: 1,
				y: 0,
				duration: 0.8,
				scale: 1,
				ease: 'elastic.out(1,0.3)'
			}
		);
	});



</script>

<!--Pallax var-->



<section data-slice-type={slice.slice_type} data-slice-variation={slice.variation} class="">
	<div>
		<h3>{scroll}</h3>
	</div>
    <div class="mx-auto w-full">
	<div class="absolute bg-fixed bg-cover mx-auto w-full h-200" style="background-image: url(../../../../static/1Stars.svg);">
		<div class="inset-0 absolute bg-fixed bg-cover mx-auto w-full h-200"  style="background-image: url(../../../../static/3Mountain.svg);"/> 
        <div class="inset-0 absolute bg-fixed bg-cover mx-auto w-full h-200"  style="background-image: url(../../../../static/4Mountain.svg);"/>
		<div class="inset-0 absolute bg-fixed bg-cover mx-auto w-full h-200"  style="background-image: url(../../../../static/5Crater.svg);"/>
		<div class="grid min-h-[65vh] grid-cols-1 items-center md:grid-cols-2">
			<div class="relative z-10 row-span-1 -my-10 aspect-[1/1.3] overflow-hidden md:col-span-1 md:col-start-2 md:mt-0">
            <Scene />
        </div>
		
        <div class="col-start-1 md:row-start-1">
            <h1 class="mb-2 md:mb-8 text-[clamp(3rem,20vmin,8rem)] font-extrabold leading-none tracking-tighter text-nowrap"
            aria-label={slice.primary.welcome + ' ' + slice.primary.name}
            >
                {#if welcome_letters.length && name_letters.length}
                <span class="block text-slate-300">
                    {#each welcome_letters as letter}
                        <span class="name-animation inline-block opacity-100">{letter}</span>    
                    {/each}
                </span>
                <span class="block text-slate-500 -mt-[.2em]">
                    {#each name_letters as letter}
                        <span class="name-animation inline-block opacity-100">{letter}</span>    
                    {/each}
                </span>
                {/if}
            </h1>
            <span class="job-title block bg-gradient-to-tr from-zinc-500 via-zinc-200 to-gray-500 bg-clip-text text-transparent text-xl font-bold uppercase tracking-[.2em] md:text-4xl opacity-0">
                {slice.primary.flavor_text}
            </span>
            </div>
        </div>
	</div>
    </div>
	<div class="box"></div>
	<div class="box"></div>
	<div class="box"></div>
	<div class="box"></div>
	<div class="box"></div>
	<div class="box" ></div>
	<div class="box" style:transform={'translate3d(0, ${scroll * 2}px, 0)'}></div>
	<div class="box translate3d_image" />
</section>

<style>
	.box{
		--size: 300px;
		height: var(--size);
		width: var(--size);
		background: lightgreen;
		margin-bottom: 1rem;
	}
	h3{
		position: fixed;
		z-index: 10;
	}
	.translate3d_image { 
            transform: translate3d(100px, 0, 0); 
        } 
</style>