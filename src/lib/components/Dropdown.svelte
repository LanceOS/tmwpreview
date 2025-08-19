<script lang="ts">
	import { i18n, setLanguage } from '$lib/stores/Translation.store.js';
	import Icon from '@iconify/svelte';

	const languageCodes = ['en', 'es', 'ar', 'fr', 'de', 'hi', 'zh', 'ko', 'ja', 'ru', 'pt'];

	let isDropdownOpen = false;
	let isAccordionOpen = false;
	let selectedLang = 'en';

	const toggleDropdown = () => {
		isDropdownOpen = !isDropdownOpen;
	};

	const toggleAccordion = () => {
		isAccordionOpen = !isAccordionOpen;
	};

	const selectLanguage = (lang: string) => {
		selectedLang = lang;
		setLanguage(lang);
		isDropdownOpen = false;
		isAccordionOpen = false;
	};
</script>

{#snippet Language(langs: any)}
	{#each langs as lang}
		<button
			onclick={() => selectLanguage(lang)}
			class="block w-full cursor-pointer px-4 py-2 text-left text-slate-700 transition-colors hover:bg-slate-100"
		>
			{$i18n.t(`navigation.navLanguages.${lang}`)}
		</button>
	{/each}
{/snippet}

<!-- Desktop Dropdown -->
<div class="relative hidden md:block">
	<button
		onclick={toggleDropdown}
		class="flex cursor-pointer items-center space-x-2 rounded-full px-4 py-2 font-medium text-slate-600 transition-colors duration-200 hover:text-indigo-600"
	>
		<Icon icon="lucide:globe" class="h-5 w-5" />
		<span>{selectedLang.toUpperCase()}</span>
		<Icon icon="lucide:chevron-down" class="h-4 w-4 transform transition-transform duration-200" />
	</button>

	{#if isDropdownOpen}
		<div
			class="absolute right-0 z-50 mt-2 w-fit rounded-lg border border-slate-200 bg-white py-1 shadow-lg"
		>
			{@render Language(languageCodes)}
		</div>
	{/if}
</div>

<div class="block md:hidden w-full">
	<button
		onclick={toggleAccordion}
		class="flex w-full justify-between items-center px-4 py-2 text-slate-600 font-medium hover:text-indigo-600"
	>
		<div class="flex items-center space-x-2">
			<Icon icon="lucide:globe" class="h-5 w-5" />
			<span>{selectedLang.toUpperCase()}</span>
		</div>
		<Icon icon={isAccordionOpen ? "lucide:chevron-up" : "lucide:chevron-down"} class="h-4 w-4" />
	</button>

	{#if isAccordionOpen}
		<div class="mt-2 max-h-48 overflow-y-auto rounded-md border border-slate-200 bg-white shadow-inner">
			{@render Language(languageCodes)}
		</div>
	{/if}
</div>
