<!-- src/lib/components/SkillPill.svelte -->
<script>
	export let skill;
</script>

<div class="pill">
	{skill}
</div>

<style>
	.pill {
		background: #e0f2f1;
		color: #004d40;
		padding: 0.5rem 1rem;
		border-radius: 10px;
		text-align: center;
		font-weight: 500;
		transition: transform 0.2s;
		display: inline-block; /* Changed to inline-block for variable width */
		margin: 0.25rem; /* Added margin to make pills closer together */

		/* &:hover {
			transform: translateY(-2px);
			cursor: default;
		} */
	}
</style>
