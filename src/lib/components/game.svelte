{#await import('$lib/components/phaser-container.svelte')}
	<div class="font-monospace text-3xl">Downloading ...</div>
{:then { default: PhaserContainer }}
	<PhaserContainer />
{:catch error}
	<div class="font-monospace">
		Something went wrong: {error.message}
	</div>
{/await}
