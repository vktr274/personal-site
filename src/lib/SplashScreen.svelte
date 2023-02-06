<script lang="ts">
	import { onMount } from 'svelte';

	export let staticText: string;
	export let loopedText: string[];
	export let headline: string;

	let index = 0;
	let transitionElement: HTMLElement;
	let loopedTextElement: HTMLElement;

	const onScroll = () => {
		if (window.scrollY > 0) {
			transitionElement.classList.add('splash-transition--active');
		} else {
			transitionElement.classList.remove('splash-transition--active');
		}
	};

	onMount(() => {
		setInterval(() => {
			loopedTextElement.classList.remove('animate__fadeInDown');
			loopedTextElement.classList.add('animate__fadeOutDown');
			setTimeout(() => {
				loopedTextElement.innerHTML = loopedText[index];
				loopedTextElement.classList.remove('animate__fadeOutDown');
				loopedTextElement.classList.add('animate__fadeInDown');
				index = (index + 1) % loopedText.length;
			}, 500);
		}, 4000);
	});
</script>

<svelte:window on:scroll={onScroll} />

<div class="hero fullscreen hero-img parallax-img">
	<div class="hero-body">
		<div class="content u-text-center u-unselectable">
			<h1 class="headline-3">{headline}</h1>
			<h5 class="m-0">{staticText}</h5>
			<h5
				id="looped-text"
				class="m-0 text-gray-600 animate__animated animate__fadeInDown animate__faster"
				bind:this={loopedTextElement}
			>
				{loopedText[loopedText.length - 1]}
			</h5>
		</div>
	</div>
	<div bind:this={transitionElement} class="splash-transition" />
</div>

<style lang="scss">
	.hero-img {
		background-image: url('/images/splash.jpg');
	}
	.splash-transition {
		background-image: linear-gradient(180deg, hsla(0, 0%, 100%, 0.0001), #fff);
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;
		height: 175px;
		transition: all 0.3s ease;
		opacity: 0;
		&:global(.splash-transition--active) {
			opacity: 1;
		}
	}
</style>
