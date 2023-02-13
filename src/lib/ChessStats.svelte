<script lang="ts">
	export let id: string;
	export let username: string;

	const getStats = async () => {
		return fetch(`https://api.chess.com/pub/player/${username}/stats`).then((response) =>
			response.json()
		);
	};
</script>

<div {id} class="mx-auto max-w-md background-image">
	<div class="u-center-alt">
		<div class="row">
			<div class="col u-text-center">
				<h2 class="text-white">Chess Stats</h2>
				<span class="usquare">
					<a
						class="utb utb-OLR"
						href="https://www.chess.com/member/{username}"
						target="_blank"
						rel="noopener noreferrer"
					>
						@{username}
					</a>
				</span>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<div class="content u-text-center pt-3">
					{#await getStats()}
						<span class="icon rotate text-white" style:font-size="28px">
							<i class="fas fa-chess-board fa-wrapper" />
						</span>
						<p class="text-white">Loading...</p>
					{:then stats}
						<div class="tag-container">
							<div class="tag tag--rounded u-shadow-lg text-indigo-500 bg-indigo-100">
								<span class="font-bold">Bullet&nbsp;</span>
								{stats.chess_bullet.last.rating}
							</div>
							<div class="tag tag--rounded u-shadow-lg text-indigo-500 bg-indigo-100">
								<span class="font-bold">Blitz&nbsp;</span>
								{stats.chess_blitz.last.rating}
							</div>
							<div class="tag tag--rounded u-shadow-lg text-indigo-500 bg-indigo-100">
								<span class="font-bold">Rapid&nbsp;</span>
								{stats.chess_rapid.last.rating}
							</div>
						</div>
					{/await}
				</div>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	@keyframes rotate {
		0% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg);
		}
	}
	.rotate {
		animation: rotate 2s cubic-bezier(0.68, -0.55, 0.27, 1.55) infinite;
	}
	.background-image {
		position: relative;
		min-height: 100vh;
		&::before {
			content: '';
			position: absolute;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;
			background-image: url('/images/chess.svg');
			background-repeat: no-repeat;
			background-position: center;
			background-size: 100vh;
			opacity: 0.1;
		}
	}
</style>
