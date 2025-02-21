<!-- src/lib/components/ExperienceCard.svelte -->
<script>
	export let company;
	export let role;
	export let period;
	export let link;
	export let highlights;

	let isExpanded = false;

	function toggleExpand() {
		isExpanded = !isExpanded;
	}

	/**
	 * @param {string | number | Date} start
	 * @param {string | number | Date} end
	 */
	function calculateDuration(start, end) {
		const startDate = new Date(start);
		const endDate = end.toString().toLowerCase() === 'present' ? new Date() : new Date(end);
		const diff = endDate.getTime() - startDate.getTime();
		const diffMonths = Math.floor(diff / (1000 * 60 * 60 * 24 * 30)) + 1; // +1 to include the start month
		const years = Math.floor(diffMonths / 12);
		const months = diffMonths % 12;

		return `${years ? years + ' yr ' : ''}${months ? months + ' mos' : ''}`.trim();
	}

	const duration = calculateDuration(period.split(' - ')[0], period.split(' - ')[1]);
</script>

<div class="card" on:click={toggleExpand}>
	<div class="card-header">
		<h3>
			<strong>{role}</strong> @
			{#if link}
				<a href={link} target="_blank" class="company-link">{company}</a>
			{:else}
				{company}
			{/if}
		</h3>
		<span class="period">{period} · {duration}</span>
	</div>
	{#if isExpanded}
		<ul class="highlights">
			{#each highlights as highlight}
				<li>✍️ {highlight}</li>
			{/each}
		</ul>
	{/if}
	<div class="arrow">{isExpanded ? '⌃' : '⌵'}</div>
</div>

<style>
	.card {
		background: white;
		border-radius: 8px;
		padding: 1.5rem;
		margin-bottom: 1.5rem;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
		transition: transform 0.2s;
		cursor: pointer;
		position: relative;

		&:hover {
			transform: translateY(-2px);
		}
	}

	.card-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 1rem;
    font-size: large;
	}

	.company-link {
		color: #009688;
		text-decoration: none;

		&:hover {
			text-decoration: underline;
		}
	}

	.highlights {
		margin-top: 0.5rem;

		li {
			margin-bottom: 0.5rem;
			line-height: 1.5;
		}
	}

	.arrow {
		position: absolute;
		bottom: -0.3rem;
		left: 50%;
		transform: translateX(-50%);
		font-size: 2rem;
		color: #6e7e7c;
	}
</style>
