<script lang="ts">
	export let id: string;
	export let username: string;

	const getStats = async () => {
		return fetch(`https://api.chess.com/pub/player/${username}/stats`).then((response) =>
			response.json()
		);
	};
</script>

<div {id} class="mx-auto max-w-md">
	<div class="row">
		<div class="col u-text-center">
			<h2>Chess Stats</h2>
		</div>
	</div>
	<div class="row">
		<div class="col">
			<div class="content u-text-center pt-3">
				{#await getStats()}
					<span class="icon rotate" style:font-size="28px">
						<i class="fas fa-chess-board fa-wrapper" />
					</span>
					<p>Loading...</p>
				{:then stats}
					<div class="tag-container">
						<div class="tag tag--md tag--rounded">
							<span class="uppercase font-bold">Bullet&nbsp;</span>
							{stats.chess_bullet.last.rating}
						</div>
						<div class="tag tag--md tag--rounded">
							<span class="uppercase font-bold">Blitz&nbsp;</span>
							{stats.chess_blitz.last.rating}
						</div>
						<div class="tag tag--md tag--rounded">
							<span class="uppercase font-bold">Rapid&nbsp;</span>
							{stats.chess_rapid.last.rating}
						</div>
					</div>
				{/await}
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
</style>
