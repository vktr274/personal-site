<script lang="ts">
	import { onMount } from 'svelte';

	export let staticText: string;
	export let loopedText: string[];
	export let headline: string;

	let index = 0;

	onMount(() => {
		const text = document.querySelector('#looped-text');
		setInterval(() => {
			text?.classList.remove('animate__fadeInDown');
			text?.classList.add('animate__fadeOutDown');
			setTimeout(() => {
				text!.innerHTML = loopedText[index];
				text?.classList.remove('animate__fadeOutDown');
				text?.classList.add('animate__fadeInDown');
				index = (index + 1) % loopedText.length;
			}, 500);
		}, 4000);
	});
</script>

<div class="hero fullscreen hero-img parallax-img">
	<div class="hero-body">
		<div class="content u-text-center u-unselectable">
			<h1 class="headline-3">{headline}</h1>
			<h5 class="m-0">{staticText}</h5>
			<h5
				id="looped-text"
				class="m-0 text-gray-600 animate__animated animate__fadeInDown animate__faster"
			>
				{loopedText[loopedText.length - 1]}
			</h5>
		</div>
	</div>
</div>

<style lang="scss">
	.hero-img {
		background-image: url('/images/splash.jpg');
	}
</style>
