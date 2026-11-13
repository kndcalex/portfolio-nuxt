<script setup lang="ts">
import { Menu, X } from '@lucide/vue'

const route = useRoute()
const menuOpen = ref(false)
defineProps<{ scrollProgress: number; activeSection: string }>()

const links = [
  { label: 'Home', to: '/#home', hash: '#home' },
  { label: 'About Me', to: '/#about', hash: '#about' },
  { label: 'Tech Stack', to: '/#stack', hash: '#stack' },
  { label: 'Certifications', to: '/#certifications', hash: '#certifications' },
  { label: 'Contact', to: '/#contact', hash: '#contact' }
]

watch(() => route.fullPath, () => {
  menuOpen.value = false
})

</script>

<template>
  <header class="navbar fixed inset-x-0 top-0 z-50 min-h-16 border-b border-base-300 bg-base-200/95 px-4 backdrop-blur sm:px-6">
    <div class="mx-auto flex w-full max-w-7xl items-center justify-between">
      <NuxtLink to="/" class="flex items-center gap-3 rounded-lg no-underline" aria-label="John Kendrick Cabunilas home">
        <span class="grid size-10 shrink-0 place-items-center rounded-full bg-primary font-bold text-primary-content">JK</span>
        <span class="hidden text-sm font-semibold text-base-content sm:inline">John Kendrick Cabunilas</span>
      </NuxtLink>

      <nav class="hidden items-center gap-1 md:flex" aria-label="Main navigation">
        <NuxtLink
          v-for="link in links"
          :key="link.to"
          :to="link.to"
          class="rounded-lg px-3 py-2 text-sm font-medium text-base-content/70 transition-colors hover:bg-base-300 hover:text-primary"
          :class="{ 'bg-base-300 text-primary': activeSection === link.hash }"
          :aria-current="activeSection === link.hash ? 'location' : undefined"
        >
          {{ link.label }}
        </NuxtLink>
      </nav>

      <button
        type="button"
        class="btn btn-ghost btn-square md:hidden"
        :aria-expanded="menuOpen"
        aria-controls="mobile-navigation"
        :aria-label="menuOpen ? 'Close navigation menu' : 'Open navigation menu'"
        @click="menuOpen = !menuOpen"
      >
        <X v-if="menuOpen" :size="22" />
        <Menu v-else :size="22" />
      </button>
    </div>

    <nav
      v-if="menuOpen"
      id="mobile-navigation"
      class="absolute inset-x-0 top-full border-b border-base-300 bg-base-200 px-4 py-3 shadow-xl md:hidden"
      aria-label="Mobile navigation"
    >
      <NuxtLink
        v-for="link in links"
        :key="link.to"
        :to="link.to"
        class="block rounded-lg px-4 py-3 text-center text-sm font-medium text-base-content/80 hover:bg-base-300 hover:text-primary"
        :class="{ 'bg-base-300 text-primary': activeSection === link.hash }"
        :aria-current="activeSection === link.hash ? 'location' : undefined"
      >
        {{ link.label }}
      </NuxtLink>
    </nav>

    <div
      class="absolute inset-x-0 bottom-0 h-0.5 bg-base-300"
      role="progressbar"
      aria-label="Page scroll progress"
      aria-valuemin="0"
      aria-valuemax="100"
      :aria-valuenow="scrollProgress"
    >
      <div
        class="h-full origin-left bg-primary transition-transform duration-100"
        :style="{ transform: `scaleX(${scrollProgress / 100})` }"
      />
    </div>
  </header>
</template>
