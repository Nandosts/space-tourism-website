<script lang="ts">
	import './styles/global.scss';
	import { Navbar } from '$lib/modules';
	import { register, init, getLocaleFromNavigator, isLoading } from 'svelte-i18n';
	import LoadData from '$lib/modules/translation/data.svelte';
	import { browser } from '$app/environment';

	import { Loading } from '$lib/components';

	const locale = browser ? window.localStorage.getItem('Locale') : undefined;
	register('en', () => import('$lib/modules/translation/en.json'));
	register('en-US', () => import('$lib/modules/translation/en.json'));
	register('pt', () => import('$lib/modules/translation/pt-BR.json'));
	register('pt-BR', () => import('$lib/modules/translation/pt-BR.json'));

	init({
		fallbackLocale: 'en',
		initialLocale: locale || getLocaleFromNavigator()
	});
</script>

{#if $isLoading}
	<Loading />
{:else}
	<LoadData />
	<Navbar />
	<slot />
{/if}
