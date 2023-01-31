<script lang="ts">
	const headlines = ['Machine Learning Enthusiast.', 'Chess Enjoyer.', 'Developer.'];
	import { onMount } from 'svelte';
	let index = 0;

	onMount(() => {
		const headline = document.querySelector('#looped-text');
		setInterval(() => {
			headline?.classList.remove('animate__fadeInDown');
			headline?.classList.add('animate__fadeOutDown');
			setTimeout(() => {
				headline!.innerHTML = headlines[index];
				headline?.classList.remove('animate__fadeOutDown');
				headline?.classList.add('animate__fadeInDown');
				index = (index + 1) % headlines.length;
			}, 1000);
		}, 5000);
	});
</script>

<div>
	<div class="hero fullscreen hero-img parallax-img splash-img">
		<div class="hero-body">
			<div class="content u-text-center u-unselectable">
				<h1 class="headline-3">My name is Viktor</h1>
				<h5 class="m-0">I am a</h5>
				<h5 id="looped-text" class="m-0 text-gray-600 animate__animated animate__fadeInDown">
					Developer.
				</h5>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	.splash-img {
		background-image: url('images/splash.jpg');
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
	}
</style>
