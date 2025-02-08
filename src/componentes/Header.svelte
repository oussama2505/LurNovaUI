<!-- Header.svelte -->
<script lang="ts">
    import Icon from './Icon.svelte';
    export let userName = "RMBodrigo-Martinez";
    
    const navLinks = [
        { name: 'Chat', icon: 'chat' },
        { name: 'Bots', icon: 'bot' },
        { name: 'Knowledge', icon: 'knowledge' },
        { name: 'Logs', icon: 'logs' },
        { name: 'Account', icon: 'account' }
    ];
</script>

<header class="w-full border-b border-gray-200 bg-gradient-to-r from-blue-50 to-indigo-50 shadow-sm backdrop-blur-lg">
    <nav class="mx-auto flex max-w-7xl items-center justify-between px-4 py-3">
        <!-- Left Section -->
        <div class="flex items-center space-x-4">
            <a href="#" class="flex items-center space-x-2 group">
                <div class="p-2 bg-blue-600 rounded-lg group-hover:rotate-12 transition-transform">
                    <Icon name="bot" className="w-6 h-6 text-white" />
                </div>
                <span class="text-xl font-bold text-gray-900 bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
                    LurNova UI
                </span>
            </a>
            
            <div class="ml-6 flex items-center space-x-2">
                {#each navLinks as link}
                    <a href="#" class="flex items-center space-x-2 rounded-lg px-3 py-2 text-sm font-medium text-gray-600 hover:bg-white hover:text-gray-900 hover:shadow-sm transition-all duration-200">
                        <Icon name={link.icon} className="w-5 h-5" />
                        <span>{link.name}</span>
                    </a>
                {/each}
            </div>
        </div>

        <!-- Right Section -->
        <div class="flex items-center space-x-4">
            <a href="#" class="flex items-center space-x-2 rounded-lg px-3 py-2 text-sm font-medium text-gray-600 hover:bg-white hover:text-gray-900 hover:shadow-sm transition-all">
                <Icon name="help" className="w-5 h-5" />
                <span>Get Help</span>
            </a>
            
            <div class="flex items-center space-x-2 group cursor-pointer">
                <div class="flex h-9 w-9 items-center justify-center rounded-full bg-gradient-to-br from-blue-100 to-indigo-100 text-sm font-medium text-blue-800 shadow-sm group-hover:ring-2 group-hover:ring-blue-300 transition-all">
                    {userName?.[0] ?? 'U'}  <!-- Default fallback to 'U' -->
                </div>
                <span class="text-sm font-medium text-gray-700">{userName}</span>
            </div>
        </div>
    </nav>
</header>

<style lang="postcss">
    /* Animación personalizada para el logo */
    @keyframes logo-float {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-3px); }
    }
    
    .group:hover .group-hover\:rotate-12 {
        animation: logo-float 1.5s ease-in-out infinite;
    }
</style>