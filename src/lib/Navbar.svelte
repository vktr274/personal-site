<script lang="ts">
	import { onMount } from 'svelte';
	import type { IconButton, TextButton, User } from './types';

	export let user: User;
	export let iconButtons: IconButton[];
	export let textButtons: TextButton[];

	let activeNavItem = '';
	let openMenu = false;

	const triggerMenu = () => (openMenu = !openMenu);

	$: isActive = (item: string): boolean => activeNavItem === item;

	onMount(() => {
		const header = document.querySelector('.header') as HTMLElement;
		const splash = document.querySelector('.splash-img') as HTMLElement;
		let limit = splash.offsetHeight - header.offsetHeight;
		window.addEventListener('scroll', () => {
			if (window.scrollY > limit) {
				// hide header
				header.classList.add('animate__fadeOutUp');
				header.classList.remove('animate__fadeInDown');
			} else {
				// show header
				header.classList.add('animate__fadeInDown');
				header.classList.remove('animate__fadeOutUp');
			}
		});
		window.addEventListener('resize', () => {
			limit = splash.offsetHeight - header.offsetHeight;
		});
	});
</script>

<div
	class="header header-fixed u-unselectable header-animated header-clear animate__animated animate__faster"
>
	<div class="header-brand">
		<div class="nav-item no-hover my-2 mr-2">
			<div class="tile">
				<div class="tile__icon">
					<figure class="avatar avatar"><img src={user.avatar} alt="avatar" /></figure>
				</div>
				<div class="tile__container">
					<p class="tile__title m-0">{user.name}</p>
					<p class="tile__subtitle m-0">@{user.username}</p>
				</div>
			</div>
		</div>
		<a href="#menu" class="nav-item nav-btn" class:active={openMenu} on:click={triggerMenu}>
			<span />
			<span />
			<span />
		</a>
	</div>
	<div class="header-nav" class:active={openMenu}>
		<div class="nav-left">
			{#each iconButtons as button}
				<div class="nav-item hover-grow">
					<a href={button.link} target="_blank" rel="noopener noreferrer" on:click={triggerMenu}>
						<span class="icon">
							<i class={button.classes} />
						</span>
					</a>
				</div>
			{/each}
		</div>
		<div class="nav-right">
			{#each textButtons as button}
				<div class="nav-item hover-grow" class:active={isActive(button.name)}>
					<a
						href={'#' + button.name}
						on:click={() => (triggerMenu(), (activeNavItem = button.name))}
					>
						{button.text}
					</a>
				</div>
			{/each}
		</div>
	</div>
</div>
