<!-- src/lib/components/LanguageLevel.svelte -->
<script>
	export let language;
	export let level;
</script>

<div class="language-container">
	<span class="language">{language}</span>
	<div class="levels">
		{#each Array(5) as _, i}
			<div class="level-circle" class:filled={i < level}></div>
		{/each}
	</div>
</div>

<style>
	.language-container {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 1rem;
		max-width: 400px;
	}

	.levels {
		display: flex;
		gap: 0.5rem;
	}

	.level-circle {
		width: 16px;
		height: 16px;
		border-radius: 50%;
		border: 2px solid #009688;
		background: transparent;

		&.filled {
			background: #009688;
		}
	}
</style>
