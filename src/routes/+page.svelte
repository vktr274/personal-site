<script lang="ts">
	import About from '$lib/About.svelte';
	import ChessStats from '$lib/ChessStats.svelte';
	import Skills from '$lib/Skills.svelte';
	import SplashScreen from '$lib/SplashScreen.svelte';
	import type { Technology } from '$lib/types';

	const loopedText = ['Student', 'Machine Learning Enthusiast', 'Chess Enjoyer', 'Developer'];

	const name = 'Viktor Modroczký';
	const firstName = 'Viktor';
	const avatar = '/images/avatar.jpg';
	const subtitle = 'Intelligent Software Systems Student';
	const paragraph = `I'm a student at the Faculty of Informatics and Information Technologies at the University
				of Technology in Bratislava. I have a bachelor's degree in Computer Science and I'm
				currently studying Intelligent Software Systems for my master's degree. I'm interested in
				frontend web development, machine learning and chess.`;
	const technologies: Technology[] = [
		{
			name: 'Python',
			icon: 'devicon-python-plain colored',
			details: ['TensorFlow', 'Flask', 'Django', 'Jupyter Notebook']
		},
		{
			name: 'TypeScript',
			icon: 'devicon-typescript-plain colored',
			details: ['Vue', 'SvelteKit', 'Node.js', 'Quasar', 'Adonis.js']
		},
		{
			name: 'JavaScript',
			icon: 'devicon-javascript-plain colored',
			details: ['jQuery', 'ScrollMagic']
		},
		{
			name: 'Kotlin',
			icon: 'devicon-kotlin-plain colored',
			details: ['Jetpack Compose', 'Ktor', 'Exposed']
		},
		{
			name: 'Java',
			icon: 'devicon-java-plain colored',
			details: ['Spring', 'Apache Maven', 'Apache Spark', 'Hibernate']
		},
		{
			name: 'Matlab',
			icon: 'devicon-matlab-plain colored',
			details: ['Signal Processing Toolbox', 'Image Processing Toolbox', 'Wavelet Toolbox']
		},
		{
			name: 'CSS',
			icon: 'devicon-css3-plain colored',
			details: ['SCSS', 'Cirrus', 'Materialize', 'Bootstrap']
		},
		{
			name: 'Docker',
			icon: 'devicon-docker-plain colored',
			details: ['Docker Compose', 'Docker Desktop']
		},
		{
			name: 'Git',
			icon: 'devicon-git-plain colored',
			details: ['GitHub', 'GitLab', 'Git CLI']
		},
		{
			name: 'PostgreSQL',
			icon: 'devicon-postgresql-plain colored',
			details: ['pgAdmin']
		},
		{
			name: 'LaTeX',
			icon: 'devicon-latex-original text-green-400',
			details: ['Overleaf']
		}
	];
	const username = 'viktor404notfound';
</script>

<SplashScreen name={firstName} {loopedText} />
<About id="about-me" {name} {subtitle} {avatar} {paragraph} />
<Skills id="tech-stack" {technologies} />
<ChessStats id="chess-stats" {username} />
