<script lang="ts">
    import Icon from "@iconify/svelte";
    
    // Svelte 5 runes for reactive state
    let isMenuOpen = $state(false);
    let email = $state('');
    let isSubscribed = $state(false);
    
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
    
    const handleNotifyMe = () => {
        if (email.trim()) {
            isSubscribed = true;
            // Here you would typically send the email to your backend
            console.log('Email submitted:', email);
        }
    };
</script>

<svelte:head>
    <!-- SEO Meta Tags -->
    <title>The Management Workspace - Coming Soon | Simple Project Management Solution</title>
    <meta name="description" content="The Management Workspace is coming soon! Be the first to know when our simple, powerful project management solution launches. Sign up for early access and updates." />
    <meta name="keywords" content="project management coming soon, workspace management launch, team collaboration tool, project planning software, early access" />
    <meta name="author" content="The Management Workspace" />
    
    <!-- Open Graph / Social Media -->
    <meta property="og:type" content="website" />
    <meta property="og:title" content="The Management Workspace - Coming Soon" />
    <meta property="og:description" content="Get ready for the future of project management. Sign up for early access to The Management Workspace - launching soon!" />
    <meta property="og:site_name" content="The Management Workspace" />
    
    <!-- Twitter Card -->
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="The Management Workspace - Coming Soon" />
    <meta name="twitter:description" content="Revolutionary project management solution launching soon. Join the waitlist for early access!" />
    
    <!-- Additional SEO -->
    <meta name="robots" content="index, follow" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="canonical" href="https://themanagementworkspace.com" />
    
    <!-- JSON-LD Structured Data -->
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "SoftwareApplication",
        "name": "The Management Workspace",
        "description": "Simple project management solution launching soon with multi-workspace support and team collaboration tools",
        "applicationCategory": "BusinessApplication",
        "operatingSystem": "Web Browser",
        "releaseNotes": "Coming Soon - Sign up for early access",
        "featureList": [
            "Easy-to-use minimal UI",
            "Multi-workspace support",
            "Built-in messaging applications",
            "Workspace member assignments and management"
        ]
    }
    </script>
</svelte:head>

<div class="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50 to-indigo-50">
    <!-- Navigation -->
    <nav class="sticky top-0 z-50 backdrop-blur-xl bg-white/80 border-b border-slate-200/60 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center space-x-2">
                    <div class="w-8 h-8 bg-gradient-to-br from-indigo-600 to-purple-600 rounded-lg flex items-center justify-center">
                        <Icon icon="lucide:layout-grid" class="w-5 h-5 text-white" />
                    </div>
                    <h1 class="text-xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">
                        The Management Workspace
                    </h1>
                </div>
                
                <!-- Desktop Navigation -->
                <div class="hidden md:flex items-center space-x-8">
                    <button onclick={() => scrollToSection('features')} class="text-slate-600 hover:text-indigo-600 transition-colors duration-200 font-medium cursor-pointer">
                        Features
                    </button>
                    <button onclick={() => scrollToSection('coming-soon')} class="text-slate-600 hover:text-indigo-600 transition-colors duration-200 font-medium cursor-pointer">
                        Launch Timeline
                    </button>
                    <!-- <button onclick={() => scrollToSection('notify')} class="bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-6 py-2 rounded-full font-medium hover:shadow-lg hover:scale-105 transition-all duration-200 cursor-pointer">
                        Get Early Access
                    </button> -->
                </div>
                
                <!-- Mobile Menu Button -->
                <button onclick={toggleMenu} class="md:hidden p-2 rounded-lg hover:bg-slate-100 transition-colors cursor-pointer">
                    <Icon icon={isMenuOpen ? "lucide:x" : "lucide:menu"} class="w-6 h-6 text-slate-600" />
                </button>
            </div>
        </div>
        
        <!-- Mobile Navigation -->
        {#if isMenuOpen}
            <div class="md:hidden bg-white/95 backdrop-blur-xl border-t border-slate-200/60">
                <div class="px-4 py-6 space-y-4">
                    <button onclick={() => scrollToSection('features')} class="block w-full text-left text-slate-600 hover:text-indigo-600 transition-colors font-medium cursor-pointer">
                        Features
                    </button>
                    <button onclick={() => scrollToSection('coming-soon')} class="block w-full text-left text-slate-600 hover:text-indigo-600 transition-colors font-medium cursor-pointer">
                        Launch Timeline
                    </button>
                    <button onclick={() => scrollToSection('notify')} class="w-full bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-6 py-3 rounded-full font-medium hover:shadow-lg transition-all duration-200 cursor-pointer">
                        Get Early Access
                    </button>
                </div>
            </div>
        {/if}
    </nav>

    <!-- Hero Section -->
    <section class="relative overflow-hidden py-20 lg:py-32">
        <div class="absolute inset-0 bg-gradient-to-r from-indigo-600/5 to-purple-600/5"></div>
        <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <div class="inline-flex items-center space-x-2 bg-amber-100 px-4 py-2 rounded-full border border-amber-200 mb-8">
                <Icon icon="lucide:clock" class="w-4 h-4 text-amber-600" />
                <span class="text-sm font-medium text-amber-700">Launching Soon</span>
            </div>
            
            <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold text-slate-900 leading-tight mb-6">
                The Minimal
                <span class="bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent block">
                    Project Management Solution
                </span>
                <span class="text-2xl md:text-3xl lg:text-4xl text-slate-600 block mt-2">is Coming Soon</span>
            </h1>
            
            <p class="text-xl text-slate-600 max-w-3xl mx-auto mb-10 leading-relaxed">
                We're building the <strong>simple project management solution</strong> your team has been waiting for. 
                Clean interface, powerful features, seamless collaboration - all launching soon.
            </p>
            
            <div class="flex flex-col sm:flex-row gap-4 justify-center items-center">
                <!-- <button onclick={() => scrollToSection('notify')} class="group bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-8 py-4 rounded-2xl font-semibold text-lg hover:shadow-2xl hover:shadow-indigo-500/25 transform hover:scale-105 transition-all duration-300 flex items-center space-x-2 cursor-pointer">
                    <span>Join the Waitlist</span>
                    <Icon icon="lucide:bell" class="w-5 h-5 group-hover:rotate-12 transition-transform" />
                </button> -->
                <button onclick={() => scrollToSection('features')} class="bg-white/80 backdrop-blur-sm text-slate-700 px-8 py-4 rounded-2xl font-semibold text-lg border border-slate-200 hover:bg-white hover:shadow-xl transition-all duration-300 flex items-center space-x-2 cursor-pointer">
                    <Icon icon="lucide:eye" class="w-5 h-5" />
                    <span>Preview Features</span>
                </button>
            </div>
        </div>
        
        <!-- Floating Elements -->
        <div class="absolute top-20 left-10 w-20 h-20 bg-gradient-to-br from-indigo-400/20 to-purple-400/20 rounded-3xl rotate-12 animate-pulse"></div>
        <div class="absolute bottom-20 right-10 w-32 h-32 bg-gradient-to-br from-purple-400/20 to-pink-400/20 rounded-full animate-pulse delay-1000"></div>
    </section>

    <!-- Features Preview Section -->
    <section id="features" class="py-20 lg:py-32 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <div class="inline-flex items-center space-x-2 bg-indigo-50 px-4 py-2 rounded-full mb-6">
                    <Icon icon="lucide:eye" class="w-4 h-4 text-indigo-600" />
                    <span class="text-sm font-medium text-indigo-700">Feature Preview</span>
                </div>
                <h2 class="text-3xl md:text-5xl font-bold text-slate-900 mb-4">
                    What's Coming in
                    <span class="bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">Version 1.0</span>
                </h2>
                <p class="text-xl text-slate-600 max-w-2xl mx-auto">
                    Get a sneak peek at the powerful features we're crafting for launch day
                </p>
            </div>
            
            <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-indigo-200 hover:shadow-2xl hover:shadow-indigo-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-indigo-500 to-indigo-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:layout-dashboard" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Easy-to-use minimal UI</h3>
                    <p class="text-slate-600 leading-relaxed">Focus on your projects, not on complex software. Our clean interface makes management intuitive and effortless.</p>
                    <div class="absolute top-4 right-4 bg-emerald-100 text-emerald-700 text-xs px-2 py-1 rounded-full font-medium">
                        Ready
                    </div>
                </article>
                
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-purple-200 hover:shadow-2xl hover:shadow-purple-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-purple-500 to-purple-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:folders" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Multi-workspace support</h3>
                    <p class="text-slate-600 leading-relaxed">Seamlessly manage multiple teams, clients, or projects from a single account, keeping everything organized.</p>
                    <div class="absolute top-4 right-4 bg-emerald-100 text-emerald-700 text-xs px-2 py-1 rounded-full font-medium">
                        Ready
                    </div>
                </article>
                
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-emerald-200 hover:shadow-2xl hover:shadow-emerald-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-emerald-500 to-emerald-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:message-square" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Built-in messaging applications</h3>
                    <p class="text-slate-600 leading-relaxed">Communicate with your team directly within your workspaces to keep all project discussions in one place.</p>
                    <div class="absolute top-4 right-4 bg-amber-100 text-amber-700 text-xs px-2 py-1 rounded-full font-medium">
                        In Progress
                    </div>
                </article>
                
                <article class="group relative bg-white/80 backdrop-blur-sm p-8 rounded-3xl border border-slate-200/60 hover:border-orange-200 hover:shadow-2xl hover:shadow-orange-500/10 transition-all duration-500 hover:-translate-y-2">
                    <div class="w-16 h-16 bg-gradient-to-br from-orange-500 to-orange-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <Icon icon="lucide:users" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Workspace member assignments and management</h3>
                    <p class="text-slate-600 leading-relaxed">Easily add, manage, and assign tasks to team members within each workspace for clear responsibilities.</p>
                    <div class="absolute top-4 right-4 bg-emerald-100 text-emerald-700 text-xs px-2 py-1 rounded-full font-medium">
                        Ready
                    </div>
                </article>
            </div>
        </div>
    </section>

    <!-- Coming Soon Timeline Section -->
    <section id="coming-soon" class="py-20 lg:py-32 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-indigo-600/5 to-purple-600/5"></div>
        <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <div class="inline-flex items-center space-x-2 bg-gradient-to-r from-indigo-50 to-purple-50 px-4 py-2 rounded-full mb-8">
                <Icon icon="lucide:calendar" class="w-4 h-4 text-indigo-600" />
                <span class="text-sm font-medium bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">Launch Timeline</span>
            </div>
            
            <h2 class="text-3xl md:text-5xl font-bold text-slate-900 mb-6">
                Coming Soon!
            </h2>
            
            <p class="text-xl text-slate-600 max-w-3xl mx-auto mb-12">
                We are in the final stages of development and testing. Get ready for the launch of The Management Workspace 
                with advanced reporting, custom workflows, and integrations with your favorite tools.
            </p>
            
            <div class="grid md:grid-cols-2 gap-8 max-w-3xl mx-auto">
                <div class="bg-white/60 backdrop-blur-sm p-8 rounded-2xl border border-slate-200/60">
                    <div class="w-16 h-16 bg-gradient-to-br from-blue-500 to-blue-600 rounded-xl flex items-center justify-center mb-6 mx-auto">
                        <Icon icon="lucide:bar-chart-3" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Advanced Reporting</h3>
                    <p class="text-slate-600">Deep insights into team performance, project metrics, and productivity analytics to help you make data-driven decisions.</p>
                    <div class="mt-4 bg-blue-100 text-blue-700 text-sm px-3 py-1 rounded-full inline-block font-medium">
                        Coming Soon
                    </div>
                </div>
                
                <div class="bg-white/60 backdrop-blur-sm p-8 rounded-2xl border border-slate-200/60">
                    <div class="w-16 h-16 bg-gradient-to-br from-green-500 to-green-600 rounded-xl flex items-center justify-center mb-6 mx-auto">
                        <Icon icon="lucide:workflow" class="w-8 h-8 text-white" />
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Custom Workflows</h3>
                    <p class="text-slate-600">Design and automate workflows that match your unique business processes, from simple task flows to complex project pipelines.</p>
                    <div class="mt-4 bg-green-100 text-green-700 text-sm px-3 py-1 rounded-full inline-block font-medium">
                        Coming Soon
                    </div>
                </div>
            </div>
        </div>
    </section>
<!-- 
    Email Signup Section
    <section id="notify" class="py-20 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-indigo-600 to-purple-600"></div>
        <div class="absolute inset-0 bg-black/20"></div>
        <div class="relative max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-white">
            <Icon icon="lucide:bell" class="w-16 h-16 mx-auto mb-6 text-white/90" />
            <h2 class="text-3xl md:text-5xl font-bold mb-6">
                Be the First to Know
            </h2>
            <p class="text-xl text-indigo-100 mb-10 max-w-2xl mx-auto">
                Join our waitlist to get early access, exclusive updates, and be notified the moment The Management Workspace launches.
            </p>
            
            {#if !isSubscribed}
                <div class="max-w-md mx-auto">
                    <div class="flex flex-col sm:flex-row gap-4">
                        <input 
                            bind:value={email}
                            type="email" 
                            placeholder="Enter your email address"
                            class="flex-1 px-6 py-4 rounded-2xl text-slate-900 placeholder-slate-500 font-medium focus:outline-none focus:ring-4 focus:ring-white/25"
                        />
                        <button 
                            onclick={handleNotifyMe}
                            class="bg-white text-indigo-600 px-8 py-4 rounded-2xl font-bold hover:shadow-2xl hover:scale-105 transition-all duration-300 whitespace-nowrap cursor-pointer"
                        >
                            Notify Me
                        </button>
                    </div>
                    <p class="text-sm text-indigo-200 mt-4">No spam, just important updates. Unsubscribe anytime.</p>
                </div>
            {:else}
                <div class="max-w-md mx-auto bg-white/20 backdrop-blur-sm rounded-2xl p-8">
                    <Icon icon="lucide:check-circle" class="w-12 h-12 mx-auto mb-4 text-emerald-400" />
                    <h3 class="text-2xl font-bold mb-2">You're on the list!</h3>
                    <p class="text-indigo-100">We'll send you exclusive updates and early access as we approach launch.</p>
                </div>
            {/if}
        </div>
        
         Decorative Elements
        <div class="absolute top-10 left-10 w-24 h-24 bg-white/10 rounded-full animate-pulse"></div>
        <div class="absolute bottom-10 right-10 w-16 h-16 bg-white/10 rounded-2xl rotate-45 animate-pulse delay-500"></div>
    </section> -->

    <!-- Footer -->
    <footer class="bg-slate-900 text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="flex items-center space-x-2 mb-4 md:mb-0">
                    <div class="w-8 h-8 bg-gradient-to-br from-indigo-600 to-purple-600 rounded-lg flex items-center justify-center">
                        <Icon icon="lucide:layout-grid" class="w-5 h-5 text-white" />
                    </div>
                    <span class="text-xl font-bold">The Management Workspace</span>
                </div>
                <div class="text-slate-400 text-center md:text-right">
                    <p>&copy; 2025 The Management Workspace. All rights reserved.</p>
                    <p class="text-sm mt-1">Coming soon - Building the future of project management.</p>
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