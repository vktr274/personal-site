<script lang="ts">
	import type { IconButton, TextButton, User } from './types';

	export let user: User;
	export let iconButtons: IconButton[];
	export let textButtons: TextButton[];

	let openMenu = false;
	let hideShadow = true;

	const triggerMenu = (): void => {
		openMenu = !openMenu;
	};

	let prevScrollY = 0;

	const onScroll = () => {
		if (openMenu) return;
		const header = document.querySelector('.header') as HTMLElement;
		if (window.scrollY > prevScrollY) {
			// hide header
			header.classList.add('animate__fadeOutUp');
			header.classList.remove('animate__fadeInDown');
		} else {
			// show header
			header.classList.add('animate__fadeInDown');
			header.classList.remove('animate__fadeOutUp');
		}
		hideShadow = window.scrollY == 0;
		prevScrollY = window.scrollY;
	};
</script>

<svelte:window on:scroll={onScroll} />

<div
	class="header header-fixed u-unselectable header-animated animate__animated animate__faster header-color"
	class:u-shadow-none={hideShadow}
>
	<div class="header-brand">
		<a href="#menu" class="nav-item nav-btn" class:active={openMenu} on:click={() => triggerMenu()}>
			<span />
			<span />
			<span />
		</a>
	</div>
	<div class="header-nav" class:active={openMenu}>
		<div class="nav-left">
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
			{#each iconButtons as button}
				<div class="nav-item hover-grow">
					<a href={button.link} target="_blank" rel="noopener noreferrer">
						<span class="icon">
							<i class={button.classes} />
						</span>
					</a>
				</div>
			{/each}
		</div>
		<div class="nav-right">
			{#each textButtons as button}
				<div class="nav-item hover-grow">
					<a href={'#' + button.name} on:click={triggerMenu}>
						{button.text}
					</a>
				</div>
			{/each}
		</div>
	</div>
</div>

<style lang="scss">
	.header-color {
		background-color: rgb(242, 242, 242);
	}
</style>
