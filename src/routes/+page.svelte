<script>
	let duration,
		currentTime = 1,
		volume = 1,
		playbackRate = 1,
		muted = false,
		paused = true;
	function secondsFormat(seconds = 0) {
		return new Date(seconds * 1000).toISOString().substring(14, 19);
	}
</script>

<div class="container">
	<video
		bind:duration
		bind:currentTime
		bind:playbackRate
		bind:volume
		bind:muted
		bind:paused
		poster="https://sveltejs.github.io/assets/caminandes-llamigos.jpg"
		src="https://sveltejs.github.io/assets/caminandes-llamigos.mp4"
	/>
	<div>
		<div class="control-item">
			<span>Zaman</span>
			<input type="range" min="0" max={duration} bind:value={currentTime} />
			{secondsFormat(currentTime)} - {secondsFormat(duration)}
		</div>
		<div class="control-item">
			<span>Oynatma hızı</span>
			<input type="range" min="0" max="4" bind:value={playbackRate} />
			<span>{playbackRate}</span>
		</div>
		<div class="control-item">
			<span>Ses</span>
			<input type="range" min="0" max="1" step="0.1" bind:value={volume} />
			<span>{volume}</span>
		</div>

		<button on:click={() => (paused = !paused)}>{paused ? 'oynat' : 'duraklat'}</button>
	</div>
</div>

<style>
	.container {
		widows: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.container video {
		width: min(calc(100vw - 2rem), 1000px);
	}
	.control-item {
		padding-block: 0.25rem;
	}
</style>
