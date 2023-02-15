<script lang="ts">
	import type { IconButton, TextButton, User } from './types';

	export let user: User;
	export let iconButtons: IconButton[];
	export let textButtons: TextButton[];

	let openMenu = false;

	const triggerMenu = (): void => {
		openMenu = !openMenu;
	};

	let prevScrollY = 0;
	let headerElement: HTMLElement;

	const onScroll = () => {
		if (window.scrollY > prevScrollY) {
			// hide header
			headerElement.classList.add('header-hidden');
		} else {
			// show header
			headerElement.classList.remove('header-hidden');
		}
		prevScrollY = window.scrollY;
	};
</script>

<svelte:window on:scroll={onScroll} />

<div
	class="header header-dark header-fixed u-unselectable header-animated header-animate-visibility"
	bind:this={headerElement}
>
	<div class="header-brand">
		<a href="#menu" class="nav-item nav-btn" class:active={openMenu} on:click={triggerMenu}>
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
			{#each iconButtons as iconButton}
				<div class="nav-item">
					<a href={iconButton.link} target="_blank" rel="noopener noreferrer">
						<span class="icon hover-grow">
							<i class={iconButton.classes} />
						</span>
					</a>
				</div>
			{/each}
		</div>
		<div class="nav-right">
			{#each textButtons as textButton}
				<div class="nav-item">
					<a href={'#' + textButton.name} on:click={triggerMenu}>
						<span class="hover-grow">{textButton.text}</span>
					</a>
				</div>
			{/each}
		</div>
	</div>
</div>

<!-- 
    svelte-check bug: if any dynamic class is applied to an element,
    it is not reporting unused classes present in this file and allows
    dynamic classes to work without the :global() selector
-->
<style lang="scss">
	.header {
		&.header-animate-visibility {
			transition: all 0.3s ease;
		}
		&:global(.header-hidden) {
			opacity: 0;
			transform: translateY(-100%);
		}
	}
</style>
