<script>
	import '../app.css';
	import { onMount } from 'svelte';
	import { page } from '$app/stores';

	let activeTab = 'Home';

	$: {
		if ($page.url.pathname === '/about') {
			activeTab = 'About';
		} else {
			activeTab = 'Home';
		}
	}
</script>

export const prerender = true;

<nav>
	<ul>
		<li class:active={activeTab === 'Home'}>
			<a href="/">Home</a>
		</li>
		<li class:active={activeTab === 'About'}>
			<a href="/about">About</a>
		</li>
	</ul>
</nav>

<slot />

<style>
	nav {
		background-color: #009688;
		padding: 1.2rem;
	}

	ul {
		margin-left: 1rem;
		list-style: none;
		display: flex;
		gap: 2rem;
		/* justify-content: center; */
	}

	li {
		font-size: 1.2rem;
		padding: 0.5rem 1rem;
		border-radius: 0.5rem;
		transition: background-color 0.3s ease;
		cursor: pointer;
	}

	li:hover {
		background-color: #00796b;
	}

	a {
		color: white;
		text-decoration: none;
	}

	.active a {
		font-weight: bold;
		background-color: #00796b;
		border-radius: rem;
		padding: 0.5rem 1rem;
	}
</style>
