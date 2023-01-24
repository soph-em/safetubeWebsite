<script lang="ts">
	import { prevent_default } from 'svelte/internal';
	import iphone from './appleiPhone.png';
	function scrollIntoView({ target }) {
		const el = document.querySelector(target.getAttribute('href'));
		if (!el) return;
		el.scrollIntoView({
			behavior: 'smooth'
		});
	}
</script>

<div class="flex flex-col ">
	<section class="bg-emerald-50 w-full flex flex-col items-center h-[400px] relative">
		<div class="h-full absolute flex flex-col items-center justify-center pt-[5%]">
			<h1 class=" text-5xl font-mono text-emerald-900 font-bold">SafeTube</h1>
			<h2 class=" text-3xl text-teal-900 font-mono">A parent/guardian controlled Youtube App</h2>
			<a
				class="hover:bg-emerald-900 hover:text-white border border-teal-900 rounded p-[1%] my-[5%]"
				href="#middle"
				on:click|preventDefault={scrollIntoView}>Find out more</a
			>
		</div>
	</section>
	<div id="middle" class="flex px-[10%] py-[5%]">
		<img class="flex items-start p-5" src={iphone} alt="iphone" />
	</div>

	<div class="flex px-[10%] py-[5%]">
		<img class="flex items-start p-5" src={iphone} alt="iphone" />
	</div>
	<div class="flex px-[10%] py-[5%]">
		<img class="flex items-start p-5" src={iphone} alt="iphone" />
	</div>
	<div class="flex px-[10%] py-[5%]">
		<img class="flex items-start p-5" src={iphone} alt="iphone" />
	</div>
	<div class="flex px-[10%] py-[5%]">
		<img class="flex items-start p-5" src={iphone} alt="iphone" />
	</div>
</div>

<style>
</style>
