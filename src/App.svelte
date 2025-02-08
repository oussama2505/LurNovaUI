<script lang="ts">

import Header from './componentes/Header.svelte';
import { Home, Code, MessageSquare, Brush, Headphones, Users, Briefcase, Megaphone } from 'lucide-svelte';

  type Personality = {
    title: string;
    description: string;
    color: string;
    icon: any;
  };
  let selectedPersonality: string | null = null;
  let userName = "RMBodrigo-Martinez";


  const personalities: Personality[] = [
  { title: "Factual", description: "Provides precise responses using your knowledge base.", color: "from-purple-400 to-purple-600", icon: Home },
  { title: "Technical Support", description: "Provides technical support and offers troubleshooting aid.", color: "from-blue-400 to-blue-600", icon: Code },
  { title: "Guided", description: "Conducts comprehensive guided training sessions.", color: "from-emerald-400 to-emerald-600", icon: MessageSquare },
  { title: "Creative", description: "Facilitates AI-driven creative content generation.", color: "from-pink-400 to-pink-600", icon: Brush },
  { title: "Customer Support", description: "Delivers quick, effective solutions to customer inquiries.", color: "from-amber-400 to-amber-600", icon: Headphones },
  { title: "Base AI", description: "Utilize your preferred AI model without a knowledge base.", color: "from-slate-400 to-slate-600", icon: Users },
  { title: "Employee Help Desk", description: "Assists in addressing employee inquiries and HR guidelines.", color: "from-cyan-400 to-cyan-600", icon: Briefcase },
  { title: "Marketing", description: "Contributes in strategic planning, crafting marketing and social media content.", color: "from-fuchsia-400 to-fuchsia-600", icon: Megaphone }
];
</script>

<div class="personality-interface">
  <Header userName="RMBodrigo-Martinez" />
  <!-- Header Section -->
  <div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
    <h1 class="text-2xl font-bold text-gray-900">Bienvenido, {userName}</h1>
    <p class="mt-2 text-gray-600">Aquí puedes gestionar tus bots, chats y conocimientos.</p>
</div>

  <!-- Personality Grid -->
  <div class="personality-grid">
    {#each personalities as personality (personality.title)}
  <button
    type="button"
    class="personality-card {selectedPersonality === personality.title ? 'selected' : ''}"
    on:click={() => selectedPersonality = personality.title}
  >
    <div class={`bg-gradient-to-br ${personality.color} rounded-xl shadow-lg`}></div>
    <div class="card-content">
      <svelte:component this={personality.icon} class="personality-icon" />
      <h3 class="personality-title">{personality.title}</h3>
      <p class="personality-description">{personality.description}</p>
    </div>
  </button>
{/each}

  </div>

  <!-- Action Buttons -->
  <div class="action-buttons">
    <button type="button" class="cancel-btn">Cancel</button>
    <button type="button" class="create-btn" disabled={!selectedPersonality}>Create Personality</button>
  </div>
</div>

<style lang="postcss">
  .personality-interface {
    @apply max-w-7xl mx-auto p-8 bg-white dark:bg-gray-900 rounded-2xl shadow-xl;
  }

  .personality-grid {
    @apply grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 mb-10;
  }

  /* Tarjetas de personalidad */
  .personality-card {
    @apply relative overflow-hidden rounded-xl p-6 cursor-pointer transition-all duration-300 ease-in-out;
    @apply border-2 border-gray-200 dark:border-gray-700 hover:border-blue-500;
    @apply bg-white/30 dark:bg-gray-800/30 backdrop-blur-md;

    &::before {
      content: '';
      @apply absolute inset-0 bg-gradient-to-br from-transparent via-transparent to-black/10 opacity-0 transition-opacity duration-300;
    }

    &:hover::before {
      @apply opacity-20;
    }

    &.selected {
      @apply border-blue-500 dark:border-blue-400 shadow-lg;
      box-shadow: 0 10px 30px -10px rgba(59, 130, 246, 0.2);
    }

    & > div:first-child {
      @apply absolute inset-0 z-0 rounded-xl opacity-20 transition-opacity duration-300;
    }

    &.selected > div:first-child {
      @apply opacity-50;
    }
  }

  .card-content {
    @apply relative z-10 flex flex-col justify-center items-center text-center;
  }

  .personality-icon {
  @apply w-10 h-10 mb-3 text-gray-800 dark:text-gray-200;
}


  .personality-title {
    @apply text-xl font-semibold mb-2 text-gray-800 dark:text-gray-100;
  }

  .personality-description {
    @apply text-sm leading-relaxed text-gray-600 dark:text-gray-400;
  }

  /* Botones de acción */
  .action-buttons {
    @apply flex justify-end gap-4 border-t pt-8 border-gray-100 dark:border-gray-800;
  }

  .cancel-btn {
    @apply px-6 py-2.5 rounded-lg font-medium text-gray-600 dark:text-gray-300;
    @apply hover:bg-gray-50 dark:hover:bg-gray-800 transition-colors;
  }

  .create-btn {
    @apply px-6 py-2.5 rounded-lg font-medium text-white bg-blue-500;
    @apply hover:bg-blue-600 transition-colors shadow-lg shadow-blue-500/20;
    &[disabled] {
      @apply bg-gray-400 cursor-not-allowed;
    }
  }

  /* Dark mode */
  .dark {
    .personality-card {
      @apply border-gray-700;
    }

    .personality-card.selected {
      @apply border-blue-400;
      box-shadow: 0 10px 30px -10px rgba(96, 165, 250, 0.2);
    }
  }
</style>