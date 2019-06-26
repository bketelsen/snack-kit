<script>
	import { getContext } from 'svelte';

	export let segment = null;
	export let external = null;

	const current = getContext('nav');
</script>
<style>

a {
	text-decoration: none;
	cursor: pointer;
	color: #ffffff;
}
</style>
{#if external}
	<li class="nav-link"><a href={external}><slot></slot></a></li>
{:else}
	<li class="nav-link" class:active="{$current === segment}"><a rel="prefetch" href={segment}><slot></slot></a></li>
{/if}
