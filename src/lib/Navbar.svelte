<script lang="ts">
	let activeNavItem = '';
	let openMenu = false;

	const triggerMenu = () => (openMenu = !openMenu);

	$: isActive = (item: string): string => (activeNavItem === item ? ' active' : '');
</script>

<div class="header header-fixed u-unselectable header-animated header-clear">
	<div class="header-brand">
		<div class="nav-item no-hover my-2 mr-2">
			<div class="tile">
				<div class="tile__icon">
					<figure class="avatar avatar"><img src="./images/avatar.jpg" alt="avatar" /></figure>
				</div>
				<div class="tile__container">
					<p class="tile__title m-0">Viktor Modroczký</p>
					<p class="tile__subtitle m-0">@viktor404notfound</p>
				</div>
			</div>
		</div>
		<a href="#menu" class="nav-item nav-btn {openMenu ? 'active' : ''}" on:click={triggerMenu}>
			<span />
			<span />
			<span />
		</a>
	</div>
	<div class="header-nav {openMenu ? 'active' : ''}">
		<div class="nav-left">
			<div class="nav-item hover-grow">
				<a
					href="https://github.com/vktr274"
					target="_blank"
					rel="noopener noreferrer"
					on:click={triggerMenu}
				>
					<span class="icon">
						<i class="fab fa-wrapper fa-github" />
					</span>
				</a>
			</div>
			<div class="nav-item hover-grow">
				<a
					href="https://gitlab.com/vktr274"
					target="_blank"
					rel="noopener noreferrer"
					on:click={triggerMenu}
				>
					<span class="icon">
						<i class="fab fa-wrapper fa-gitlab" />
					</span>
				</a>
			</div>
			<div class="nav-item hover-grow">
				<a
					href="https://www.chess.com/member/viktor404notfound"
					target="_blank"
					rel="noopener noreferrer"
					on:click={triggerMenu}
				>
					<span class="icon">
						<i class="fa fa-wrapper fa-chess" />
					</span>
				</a>
			</div>
		</div>
		<div class="nav-right">
			<div class="hover-grow {'nav-item' + isActive('skills')}">
				<a href="#skills" on:click={() => (triggerMenu(), (activeNavItem = 'skills'))}>Skills</a>
			</div>
			<div class="hover-grow {'nav-item' + isActive('projects')}">
				<a href="#projects" on:click={() => (triggerMenu(), (activeNavItem = 'projects'))}>
					Projects
				</a>
			</div>
		</div>
	</div>
</div>
