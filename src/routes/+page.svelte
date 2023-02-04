<script lang="ts">
	import AboutMe from '$lib/AboutMe.svelte';
	import SplashScreen from '$lib/SplashScreen.svelte';

	const headline = 'My name is Viktor';
	const staticText = 'I am a';
	const loopedText = ['Student.', 'Machine Learning Enthusiast.', 'Chess Enjoyer.', 'Developer.'];

	const name = 'Viktor Modroczký';
	const avatar = '/images/avatar.jpg';
	const subtitle = 'Intelligent Software Systems Student';
	const paragraph = `I'm a student at the Faculty of Informatics and Information Technologies at the University
				of Technology in Bratislava. I have a bachelor's degree in Computer Science and I'm
				currently studying Intelligent Software Systems for my master's degree. I'm interested in
				frontend web development, machine learning and chess.`;
</script>

<SplashScreen {headline} {staticText} {loopedText} />
<AboutMe {name} {subtitle} {avatar} {paragraph} />
