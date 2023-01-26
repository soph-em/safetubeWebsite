<script lang="ts">
	import { prevent_default } from 'svelte/internal';
	import { slide } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import iphone from './appleiPhone.png';
	import purple from './purpleiPhone.jpg';
	import white from './whiteiPhone.jpg';
	import { Splide, SplideSlide } from '@splidejs/svelte-splide';
	import '@splidejs/svelte-splide/css';
	import type { SvelteComponentTyped } from 'svelte';
	// class ComponentName extends SvelteComponentTyped<{ propertyName: string }> {}
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
			<h1 class=" text-5xl font-noto-sans text-emerald-900 font-bold">SafeTube</h1>
			<h2 class=" text-3xl text-slate-800 font-noto-sans">
				A safer way for your kids to watch videos
			</h2>
			<div class="flex w-[50%] pt-[5%] justify-around">
				<a
					class="hover:bg-emerald-900 hover:text-white border border-teal-900 rounded font-noto-sans p-[2%] block object-contain text-center"
					href="#middle"
					on:click|preventDefault={scrollIntoView}>Find out more</a
				>
				<a
					class="dropbtn hover:bg-slate-900 hover:text-white border border-teal-900 rounded font-noto-sans p-[2%] block object-contain text-center"
					href="https://www.apple.com/uk/app-store/">Download now</a
				>
			</div>
		</div>
	</section>

	<div id="middle" class="flex px-[10%] py-[5%] h-[500px] bg-emerald-900">
		<img class="flex object-contain items-start" src={iphone} alt="iphone" />
		<p class="text-xl text-cyan-50 font-noto-sans pt-[5%] w-[60%]">
			Simple to download and use, keeping full control over the youtube channels your child is able
			to watch using a simple channel selector.
		</p>
	</div>
	<div class="bg-emerald-50 w-full flex flex-col items-center h-[500px] relative">
		<p class="pt-[30px] pr-[30px] text-2xl font-bold font-noto-sans text-emerald-900">Features</p>
		<Splide
			aria-label="My Favorite Images"
			class="w-[500px] pt-[50px] pl-[100px] pr-[100px] pb-[50px]"
		>
			<SplideSlide>
				<img src={iphone} class="h-[300px] flex items-center" />
			</SplideSlide>

			<SplideSlide>
				<img src={iphone} class="h-[300px]" />
			</SplideSlide>
			<SplideSlide>
				<img src={iphone} class="h-[300px]" />
			</SplideSlide>
			<SplideSlide>
				<img src={iphone} class="h-[300px]" />
			</SplideSlide>
			<SplideSlide>
				<img src={iphone} class="h-[300px]" />
			</SplideSlide>
			<SplideSlide>
				<img src={iphone} class="h-[300px]" />
			</SplideSlide>
		</Splide>
	</div>
	<div class="flex px-[10%] pl-[15%] py-[5%] h-[500px] bg-slate-700">
		<div class="flex flex-col">
			<p class="text-xl text-emerald-50 font-noto-sans pt-[5%] w-[80%]">
				Use guided access (Apple) or pinning (Android) for extra safety to stop your child
				navigating to other apps
			</p>
			<div class="flex flex-row justify-around w-[50%] pt-[5%] p-[5%]">
				<a
					class="bg-emerald-50 text-slate-800 hover:bg-emerald-900 hover:text-white border border-teal-900 rounded font-noto-sans p-[3%] block object-contain text-center"
					href="https://support.apple.com/en-gb/HT202612"
					target="_blank">Apple</a
				>
				<a
					class="bg-emerald-50 text-slate-800 hover:bg-emerald-900 hover:text-white border border-teal-900 font-noto-sans rounded p-[3%] block object-contain text-center"
					href="https://support.google.com/android/answer/9455138?hl=en-GB"
					target="_blank">Android</a
				>
			</div>
		</div>
		<img class="flex object-contain " src={iphone} alt="iphone" />
	</div>
</div>

<style>
</style>
