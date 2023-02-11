<script lang="ts">
	import type { Technology } from './types';

	export let technologies: Technology[];
	export let id: string;
</script>

<div {id} class="mx-auto max-w-md">
	<div class="row">
		<div class="col u-text-center text-white">
			<h2>My Tech Stack</h2>
		</div>
	</div>
	<div class="row">
		{#each technologies as tech}
			<div class="col">
				<div class="min-w-200px mx-2">
					<div class="content u-text-center pt-3">
						<img class="tech-icon" src={tech.icon} alt={tech.name} />
						<p class="title mt-2 text-white">{tech.name}</p>
						<div class="tag-container">
							{#each tech.details as detail}
								<div class="tag tag--rounded">
									{detail}
								</div>
							{/each}
						</div>
					</div>
				</div>
			</div>
		{/each}
	</div>
</div>

<style lang="scss">
	.tech-icon {
		margin: auto;
		width: 3.2rem;
		height: 3.2rem;
	}
	.min-w-200px {
		min-width: 256px;
	}
</style>
