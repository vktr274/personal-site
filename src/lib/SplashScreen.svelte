<script lang="ts">
	import { onMount } from 'svelte';

	export let loopedText: string[];
	export let name: string;

	let index = 0;
	let transitionElement: HTMLElement;
	let loopedTextElement: HTMLElement;

	const onScroll = () => {
		if (window.scrollY > 0) {
			transitionElement.classList.add('gradient-active');
		} else {
			transitionElement.classList.remove('gradient-active');
		}
	};

	onMount(() => {
		setInterval(() => {
			loopedTextElement.classList.remove('text-easeInDown');
			loopedTextElement.classList.add('text-easeOutDown');
			setTimeout(() => {
				loopedTextElement.innerHTML = loopedText[index];
				loopedTextElement.classList.remove('text-easeOutDown');
				loopedTextElement.classList.add('text-easeInDown');
				index = (index + 1) % loopedText.length;
			}, 550);
		}, 3550);
	});
</script>

<svelte:window on:scroll={onScroll} />

<div class="hero fullscreen hero-img parallax-img u-relative">
	<div class="hero-body">
		<div class="content u-text-center u-unselectable">
			<h1 class="headline-3">
				<span class="text-white">My name is</span>
				<span class="text-teal-400">{name}</span>
			</h1>
			<h3 class="m-0 text-gray-500">I am a</h3>
			<h3 id="looped-text" class="m-0 text-gray-500 text-easeInDown" bind:this={loopedTextElement}>
				{loopedText[loopedText.length - 1]}
			</h3>
		</div>
	</div>
	<div bind:this={transitionElement} class="gradient" />
</div>

<style lang="scss">
	@use 'src/styles/colors.scss' as colors;
	.hero-img {
		background-image: url('/images/splash.svg');
	}
	.gradient {
		background-image: linear-gradient(180deg, hsla(0, 0%, 100%, 0.0001), colors.$bg-color);
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;
		height: 175px;
		transition: all 0.3s ease;
		opacity: 0;
		&:global(.gradient-active) {
			opacity: 1;
		}
	}

	@keyframes fadeInDown {
		from {
			opacity: 0;
			transform: translateY(-30%);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
	@keyframes fadeOutDown {
		from {
			opacity: 1;
			transform: translateY(0);
		}
		to {
			opacity: 0;
			transform: translateY(30%);
		}
	}
	#looped-text {
		&:global(.text-easeInDown) {
			animation: fadeInDown 0.6s ease;
		}
		&:global(.text-easeOutDown) {
			animation: fadeOutDown 0.6s ease;
		}
	}
</style>
