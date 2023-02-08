<script lang="ts">
	import 'cirrus-ui';
	import '@fortawesome/fontawesome-free/css/all.min.css';

	import Header from '$lib/Header.svelte';
	import Footer from '$lib/Footer.svelte';
	import type { IconButton, TextButton, User } from '$lib/types';

	let user: User = {
		name: 'Viktor Modroczký',
		username: 'viktor404notfound',
		avatar: '/images/avatar.jpg'
	};

	const iconButtons: IconButton[] = [
		{ classes: 'fab fa-wrapper fa-github', link: 'https://github.com/vktr274' },
		{ classes: 'fab fa-wrapper fa-gitlab', link: 'https://gitlab.com/vktr274' },
		{ classes: 'fa fa-wrapper fa-chess', link: 'https://www.chess.com/member/viktor404notfound' }
	];

	const textButtons: TextButton[] = [
		{ text: 'About Me', name: 'about-me' },
		{ text: 'Tech Stack', name: 'tech-stack' },
		{ text: 'Chess Stats', name: 'chess-stats' }
		//{ text: 'Projects', name: 'projects' }
	];
</script>

<header>
	<nav>
		<Header {user} {iconButtons} {textButtons} />
	</nav>
</header>
<main>
	<slot />
</main>
<footer>
	<Footer />
</footer>
