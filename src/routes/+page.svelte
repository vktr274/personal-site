<script>
	import RevealScreen from '$lib/RevealScreen.svelte';
	import SplashScreen from '$lib/SplashScreen.svelte';
	const headline = 'My name is Viktor';
	const staticText = 'I am a';
	const loopedText = ['Machine Learning Enthusiast.', 'Chess Enjoyer.', 'Developer.'];
</script>

<SplashScreen {headline} {staticText} {loopedText} />
<RevealScreen />
