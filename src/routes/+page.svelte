<script lang="ts">
	import { prevent_default } from 'svelte/internal';
	import { slide } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import iphone from './appleiPhone.png';
	import purple from './purpleiPhone.jpg';
	import white from './whiteiPhone.jpg';
	function scrollIntoView({ target }) {
		const el = document.querySelector(target.getAttribute('href'));
		if (!el) return;
		el.scrollIntoView({
			behavior: 'smooth'
		});
	}

	let current = 0;
	const images = [iphone, white, purple, iphone, iphone];

	function prevImage() {
		current = current > 0 ? current - 1 : images.length - 1;
	}

	function nextImage() {
		current = current < images.length - 1 ? current + 1 : 0;
	}
</script>

<div class="flex flex-col ">
	<section class="bg-emerald-50 w-full flex flex-col items-center h-[400px] relative">
		<div class="h-full absolute flex flex-col items-center justify-center pt-[5%]">
			<h1 class=" text-5xl font-mono text-emerald-900 font-bold">SafeTube</h1>
			<h2 class=" text-3xl text-slate-800 font-mono">A safer way for your kids to watch videos</h2>
			<div class="flex w-[50%] pt-[5%] justify-around">
				<a
					class="hover:bg-emerald-900 hover:text-white border border-teal-900 rounded p-[2%] block object-contain text-center"
					href="#middle"
					on:click|preventDefault={scrollIntoView}>Find out more</a
				>
				<a
					class="hover:bg-slate-900 hover:text-white border border-teal-900 rounded p-[2%] block object-contain text-center"
					href="#middle"
					on:click|preventDefault={scrollIntoView}>Download now</a
				>
			</div>
		</div>
	</section>

	<div id="middle" class="flex px-[10%] py-[5%] h-[500px] bg-emerald-900">
		<img class="flex object-contain items-start" src={iphone} alt="iphone" />
		<p class="text-xl text-cyan-50 font-mono pt-[5%]">
			Keep full control over the channels your child is able to watch using a simple channel
			selector
		</p>
	</div>
	<div
		class="carousel flex object-contain h-[500px]"
		transition:slide={{ delay: 250, duration: 300, easing: quintOut }}
	>
		{#key current}
			<img
				src={images[current - 1 < 0 ? images.length - 1 : current - 1]}
				alt={`Image ${current - 1 < 0 ? images.length : current}`}
				class="prev-image h-[200px]"
				transition:slide={{ delay: 250, duration: 300, easing: quintOut }}
			/>

			<img
				src={images[current]}
				alt={`Image ${current + 1}`}
				class="current-image h-[200px]"
				transition:slide={{ delay: 250, duration: 300, easing: quintOut }}
			/>

			<img
				src={images[current + 1 > images.length - 1 ? 0 : current + 1]}
				alt={`Image ${current + 2 > images.length ? 1 : current + 2}`}
				class="next-image h-[200px]"
				transition:slide={{ delay: 250, duration: 300, easing: quintOut }}
			/>
		{/key}
	</div>

	<button on:click={prevImage}>Previous</button>
	<button on:click={nextImage}>Next</button>
	<div class="flex px-[10%] py-[5%] h-[500px] bg-slate-700">
		<img class="flex object-contain p-5" src={iphone} alt="iphone" />
		<p class="text-xl text-emerald-50 font-mono pt-[5%]">
			Use guided access to stop your child navigating to other apps -
			https://support.apple.com/en-gb/HT202612
		</p>
	</div>
</div>

<style>
</style>
