<script>
	import { page } from '$app/stores';
	import logo from './icon.png';

	import { User } from 'svelte-hero-icons';
	import Icon from 'svelte-hero-icons/Icon.svelte';
</script>

<header>
	<div class="corner">
		<a href="https://kit.svelte.dev">
			<img src={logo} alt="SvelteKit" />
		</a>
	</div>

	<nav>
		<ul>
			<li class:active={$page.path === '/'}><a sveltekit:prefetch href="/">Home</a></li>
			<li class:active={$page.path === '/recent'}><a sveltekit:prefetch href="/recent">Recent</a></li>
			<li class:active={$page.path === '/unread'}><a sveltekit:prefetch href="/unread">Unread</a></li>
		</ul>
	</nav>

	<div class="corner">
		<a sveltekit:prefetch href="/user" class="user-link">
			<Icon src="{User}" size="24" />
			<span class="label">Log in</span>
		</a>
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		background: linear-gradient(to right, rgb(47, 53, 73), rgb(63, 72, 99));
	}

	.corner {
		flex: 0 1 auto;
		padding: .4em .3em .1em .3em;
	}

	.corner .user-link {
		display: inline-block;
		padding: .3em .3em .2em .3em;
		color: var(--secondary-color);
		font-weight: 500;
		transition: color .2s;
	}

	.corner .user-link:hover {
		color: var(--pure-white);
		text-decoration: none;
	}

	.corner .user-link .label {
		display: none;
	}

	nav {
		flex: 1;
		display: flex;
		justify-content: center;
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	nav a {
		position: relative;
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 1em;
		color: var(--secondary-color);
		font-weight: 500;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a::after {
		--size: 6px;
		content: '';
		height: 3px;
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		background: var(--accent-color);
		opacity: 0;
		transition: opacity 0.2s;
	}

	a:hover {
		color: var(--pure-white);
	}

	a:hover::after {
		opacity: 0.65;
	}

	li.active a {
		color: var(--pure-white);
	}

	li.active a::after {
		opacity: 1;
	}


	@media (min-width: 720px) {
		.corner .user-link .label {
			display: inline;
		}
	}
</style>
