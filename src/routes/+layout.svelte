<script lang="ts">
	import 'cirrus-ui';
	import '@fortawesome/fontawesome-free/css/all.min.css';
	import 'animate.css';
	import Navbar from '$lib/Navbar.svelte';
	import Footer from '$lib/Footer.svelte';
</script>

<header>
	<nav>
		<Navbar />
	</nav>
</header>
<main>
	<slot />
</main>
<footer>
	<Footer />
</footer>
