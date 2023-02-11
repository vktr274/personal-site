<script lang="ts">
	export let name: string;
	export let avatar: string;
	export let subtitle: string;
	export let paragraph: string;
	export let id: string;
</script>

<div {id} class="frame max-w-sm px-4 my-8 u-shadow-none mx-auto">
	<div class="frame__header u-text-center">
		<figure class="avatar">
			<img src={avatar} alt="avatar" />
		</figure>
		<h6 class="frame__title text-white">{name}</h6>
		<div class="frame__subtitle text-gray-500">{subtitle}</div>
	</div>
	<div class="divider m-0" />
	<div class="frame__body text-white">
		<div class="content u-text-center">
			<h2>About Me</h2>
			<p>
				{paragraph}
			</p>
		</div>
	</div>
	<div class="divider m-0" />
</div>
