<script lang="ts">
	import { onMount, onDestroy } from 'svelte'
	import launchGame, { type Game } from '@/game/main'

	let gameInstance: Game | null = null
	const containerId = 'game-container'

	onMount(() => {
		gameInstance = launchGame(containerId)
	})

	onDestroy(() => {
		gameInstance?.destroy(false)
	})
</script>

<div id={containerId}></div>
