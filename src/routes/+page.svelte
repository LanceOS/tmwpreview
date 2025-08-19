<script lang="ts">
    import Icon from "@iconify/svelte";
    import { i18n } from '$lib/stores/Translation.store.js';
    import Dropdown from '$lib/components/Dropdown.svelte';
	import Navbar from "$lib/components/Navbar.svelte";
    
    // Svelte 5 runes for reactive state
    let isMenuOpen = $state(false);
    
    const toggleMenu = () => {
        isMenuOpen = !isMenuOpen;
    };
    
    const scrollToSection = (sectionId: string) => {
        const element = document.getElementById(sectionId);
        if (element) {
            element.scrollIntoView({ behavior: 'smooth' });
        }
        isMenuOpen = false;
    };
</script>

<svelte:head>
    <title>{$i18n.t("seo.title")}</title>
    <meta name="description" content="{$i18n.t("seo.description")}" />
    <meta name="keywords" content="{$i18n.t("seo.keywords")}" />
    <meta name="author" content="{$i18n.t("seo.author")}" />
    
    <meta property="og:type" content="website" />
    <meta property="og:title" content="{$i18n.t("seo.og.title")}" />
    <meta property="og:description" content="{$i18n.t("seo.og.description")}" />
    <meta property="og:site_name" content="{$i18n.t("seo.og.site_name")}" />
    
    <meta name="twitter:card" content="{$i18n.t("seo.twitter.card")}" />
    <meta name="twitter:title" content="{$i18n.t("seo.twitter.title")}" />
    <meta name="twitter:description" content="{$i18n.t("seo.twitter.description")}" />
    
    <meta name="robots" content="index, follow" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="canonical" href="https://themanagementworkspace.com" />
    
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "SoftwareApplication",
        "name": "{$i18n.t("seo.schema.name")}",
        "description": "{$i18n.t("seo.schema.description")}",
        "applicationCategory": "BusinessApplication",
        "operatingSystem": "Web Browser",
        "releaseNotes": "{$i18n.t("seo.schema.releaseNotes")}",
        "featureList": [
            "{$i18n.t("seo.schema.featureList.0")}",
            "{$i18n.t("seo.schema.featureList.1")}",
            "{$i18n.t("seo.schema.featureList.2")}",
            "{$i18n.t("seo.schema.featureList.3")}"
        ]
    }
    </script>
</svelte:head>

<div class="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50 to-indigo-50">
    <Navbar />

    <section class="relative overflow-hidden py-20 lg:py-32">
        <div class="absolute inset-0 bg-gradient-to-r from-indigo-600/5 to-purple-600/5"></div>
        <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <div class="inline-flex items-center space-x-2 bg-amber-100 px-4 py-2 rounded-full border border-amber-200 mb-8">
                <Icon icon="lucide:clock" class="w-4 h-4 text-amber-600" />
                <span class="text-sm font-medium text-amber-700">{$i18n.t("hero.status")}</span>
            </div>
            
            <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold text-slate-900 leading-tight mb-6">
                {$i18n.t("hero.title")}
                <span class="bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent block">
                    {$i18n.t("hero.title_span")}
                </span>
                <span class="text-2xl md:text-3xl lg:text-4xl text-slate-600 block mt-2">{$i18n.t("hero.subtitle")}</span>
            </h1>
            
            <p class="text-xl text-slate-600 max-w-3xl mx-auto mb-10 leading-relaxed" >
                {@html $i18n.t("hero.description")}
            </p>
            
            <div class="flex flex-col sm:flex-row gap-4 justify-center items-center">
                <button onclick={() => scrollToSection('features')} class="bg-white/80 backdrop-blur-sm text-slate-700 px-8 py-4 rounded-2xl font-semibold text-lg border border-slate-200 hover:bg-white hover:shadow-xl transition-all duration-300 flex items-center space-x-2 cursor-pointer">
                    <Icon icon="lucide:eye" class="w-5 h-5" />
                    <span>{$i18n.t("hero.cta_preview")}</span>
                </button>
            </div>
        </div>
        
        <div class="absolute top-20 left-10 w-20 h-20 bg-gradient-to-br from-indigo-400/20 to-purple-400/20 rounded-3xl rotate-12 animate-pulse"></div>
        <div class="absolute bottom-20 right-10 w-32 h-32 bg-gradient-to-br from-purple-400/20 to-pink-400/20 rounded-full animate-pulse delay-1000"></div>
    </section>

    <section id="features" class="py-20 lg:py-32 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <div class="inline-flex items-center space-x-2 bg-indigo-50 px-4 py-2 rounded-full mb-6">
                    <Icon icon="lucide:eye" class="w-4 h-4 text-indigo-600" />
                    <span class="text-sm font-medium text-indigo-700">{$i18n.t("features.title_tag")}</span>
                </div>
                <h2 class="text-3xl md:text-5xl font-bold text-slate-900 mb-4">
                    {$i18n.t("features.title")}
                    <span class="bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">{$i18n.t("features.title_span")}</span>
                </h2>
                <p class="text-xl text-slate-600 max-w-2xl mx-auto">
                    {$i18n.t("features.description")}
                </p>
            </div>
            
            <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-indigo-200 hover:shadow-2xl hover:shadow-indigo-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-indigo-500 to-indigo-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:layout-dashboard" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">{$i18n.t("features.card_ui.title")}</h3>
                    <p class="text-slate-600 leading-relaxed">{$i18n.t("features.card_ui.description")}</p>
                    <div class="absolute top-4 right-4 bg-emerald-100 text-emerald-700 text-xs px-2 py-1 rounded-full font-medium">
                        {$i18n.t("features.card_ui.status")}
                    </div>
                </article>
                
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-purple-200 hover:shadow-2xl hover:shadow-purple-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-purple-500 to-purple-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:folders" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">{$i18n.t("features.card_workspaces.title")}</h3>
                    <p class="text-slate-600 leading-relaxed">{$i18n.t("features.card_workspaces.description")}</p>
                    <div class="absolute top-4 right-4 bg-emerald-100 text-emerald-700 text-xs px-2 py-1 rounded-full font-medium">
                        {$i18n.t("features.card_workspaces.status")}
                    </div>
                </article>
                
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-emerald-200 hover:shadow-2xl hover:shadow-emerald-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-emerald-500 to-emerald-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:message-square" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">{$i18n.t("features.card_messaging.title")}</h3>
                    <p class="text-slate-600 leading-relaxed">{$i18n.t("features.card_messaging.description")}</p>
                    <div class="absolute top-4 right-4 bg-amber-100 text-amber-700 text-xs px-2 py-1 rounded-full font-medium">
                        {$i18n.t("features.card_messaging.status")}
                    </div>
                </article>
                
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-orange-200 hover:shadow-2xl hover:shadow-orange-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-orange-500 to-orange-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:users" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">{$i18n.t("features.card_assignments.title")}</h3>
                    <p class="text-slate-600 leading-relaxed">{$i18n.t("features.card_assignments.description")}</p>
                    <div class="absolute top-4 right-4 bg-emerald-100 text-emerald-700 text-xs px-2 py-1 rounded-full font-medium">
                        {$i18n.t("features.card_assignments.status")}
                    </div>
                </article>
            </div>
        </div>
    </section>

    <section id="coming-soon" class="py-20 lg:py-32 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-indigo-600/5 to-purple-600/5"></div>
        <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <div class="inline-flex items-center space-x-2 bg-gradient-to-r from-indigo-50 to-purple-50 px-4 py-2 rounded-full mb-8">
                <Icon icon="lucide:calendar" class="w-4 h-4 text-indigo-600" />
                <span class="text-sm font-medium bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">{$i18n.t("timeline.title_tag")}</span>
            </div>
            
            <h2 class="text-3xl md:text-5xl font-bold text-slate-900 mb-6">
                {$i18n.t("timeline.title")}
            </h2>
            
            <p class="text-xl text-slate-600 max-w-3xl mx-auto mb-12">
                {$i18n.t("timeline.description")}
            </p>
            
            <div class="grid md:grid-cols-2 gap-8 max-w-3xl mx-auto">
                <div class="bg-white/60 backdrop-blur-sm p-8 rounded-2xl border border-slate-200/60">
                    <div class="w-16 h-16 bg-gradient-to-br from-blue-500 to-blue-600 rounded-xl flex items-center justify-center mb-6 mx-auto">
                        <Icon icon="lucide:bar-chart-3" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">{$i18n.t("timeline.card_reporting.title")}</h3>
                    <p class="text-slate-600">{$i18n.t("timeline.card_reporting.description")}</p>
                    <div class="mt-4 bg-blue-100 text-blue-700 text-sm px-3 py-1 rounded-full inline-block font-medium">
                        {$i18n.t("timeline.card_reporting.status")}
                    </div>
                </div>
                
                <div class="bg-white/60 backdrop-blur-sm p-8 rounded-2xl border border-slate-200/60">
                    <div class="w-16 h-16 bg-gradient-to-br from-green-500 to-green-600 rounded-xl flex items-center justify-center mb-6 mx-auto">
                        <Icon icon="lucide:workflow" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">{$i18n.t("timeline.card_workflows.title")}</h3>
                    <p class="text-slate-600">{$i18n.t("timeline.card_workflows.description")}</p>
                    <div class="mt-4 bg-green-100 text-green-700 text-sm px-3 py-1 rounded-full inline-block font-medium">
                        {$i18n.t("timeline.card_workflows.status")}
                    </div>
                </div>
            </div>
        </div>
    </section>

    <footer class="bg-slate-900 text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="flex items-center space-x-2 mb-4 md:mb-0">
                    <div class="w-8 h-8 bg-gradient-to-br from-indigo-600 to-purple-600 rounded-lg flex items-center justify-center">
                        <Icon icon="lucide:layout-grid" class="w-5 h-5 text-white" />
                    </div>
                    <span class="text-xl font-bold">{$i18n.t("navigation.brand")}</span>
                </div>
                <div class="text-slate-400 text-center md:text-right">
                    <p>{$i18n.t("footer.copyright")}</p>
                    <p class="text-sm mt-1">{$i18n.t("footer.tagline")}</p>
                </div>
            </div>
        </div>
    </footer>
</div>

<style>
    @keyframes float {
        0%, 100% { transform: translateY(0px) rotate(0deg); }
        50% { transform: translateY(-20px) rotate(180deg); }
    }
    
    .animate-float {
        animation: float 6s ease-in-out infinite;
    }
</style>