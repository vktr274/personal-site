<script lang="ts">
	import About from '$lib/About.svelte';
	import Skills from '$lib/Skills.svelte';
	import SplashScreen from '$lib/SplashScreen.svelte';
	import type { Technology } from '$lib/types';

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
	const technologies: Technology[] = [
		{
			name: 'Python',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-plain.svg',
			details: ['TensorFlow', 'Flask', 'Django']
		},
		{
			name: 'TypeScript',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-plain.svg',
			details: ['Vue', 'Svelte', 'Node.js']
		},
		{
			name: 'Java',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-plain.svg',
			details: ['Spring', 'Apache Maven', 'Apache Spark']
		},
		{
			name: 'Docker',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-plain.svg',
			details: ['Docker Compose', 'Docker Desktop']
		},
		{
			name: 'Git',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-plain.svg',
			details: ['GitHub', 'GitLab']
		}
	];
</script>

<SplashScreen {headline} {staticText} {loopedText} />
<About id="about-me" {name} {subtitle} {avatar} {paragraph} />
<Skills id="tech-stack" {technologies} />
