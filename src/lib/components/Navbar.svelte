<script lang="ts">
	import Icon from "@iconify/svelte";
	import { i18n } from '$lib/stores/Translation.store.js';
	import Dropdown from '$lib/components/Dropdown.svelte';

	let isMenuOpen = $state(false);

	const toggleMenu = () => (isMenuOpen = !isMenuOpen);

	const scrollToSection = (sectionId: string) => {
		const element = document.getElementById(sectionId);
		if (element) element.scrollIntoView({ behavior: "smooth" });
		isMenuOpen = false;
	};
</script>

<nav class="sticky top-0 z-50 bg-white/80 backdrop-blur-xl border-b border-slate-200/60 shadow-sm">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex justify-between items-center h-16">
			<!-- Brand -->
			<div class="flex items-center space-x-2">
				<div class="w-8 h-8 bg-gradient-to-br from-indigo-600 to-purple-600 rounded-lg flex items-center justify-center">
					<Icon icon="lucide:layout-grid" class="w-5 h-5 text-white" />
				</div>
				<h1 class="text-xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">
					{$i18n.t("navigation.brand")}
				</h1>
			</div>

			<!-- Desktop nav -->
			<div class="hidden md:flex items-center space-x-8 relative">
				<button onclick={() => scrollToSection("features")} class="text-slate-600 hover:text-indigo-600 font-medium">
					{$i18n.t("navigation.features")}
				</button>
				<button onclick={() => scrollToSection("coming-soon")} class="text-slate-600 hover:text-indigo-600 font-medium">
					{$i18n.t("navigation.timeline")}
				</button>
				<Dropdown />
			</div>

			<!-- Mobile toggle -->
			<button onclick={toggleMenu} class="md:hidden p-2 rounded-lg hover:bg-slate-100 transition">
				<Icon icon={isMenuOpen ? "lucide:x" : "lucide:menu"} class="w-6 h-6 text-slate-600" />
			</button>
		</div>
	</div>
</nav>

{#if isMenuOpen}
	<div class="md:hidden fixed top-16 left-0 w-full bg-white/95 backdrop-blur-xl border-t border-slate-200/60 z-40 shadow-lg">
		<div class="px-4 py-6 space-y-4">
			<button onclick={() => scrollToSection("features")} class="block w-full text-left text-slate-600 hover:text-indigo-600 font-medium">
				{$i18n.t("navigation.features")}
			</button>
			<button onclick={() => scrollToSection("coming-soon")} class="block w-full text-left text-slate-600 hover:text-indigo-600 font-medium">
				{$i18n.t("navigation.timeline")}
			</button>
			<div class="w-full">
				<Dropdown />
			</div>
		</div>
	</div>
{/if}
