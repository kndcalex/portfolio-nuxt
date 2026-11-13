<script setup lang="ts">
import { ArrowUpRight, BriefcaseBusiness, Code2, House, Mail, UserRound } from '@lucide/vue'

const route = useRoute()
const links = [
  { label: 'Home', to: '/', icon: House },
  { label: 'About Me', to: '/about', icon: UserRound },
  { label: 'Tech Stack', to: '/techstack', icon: Code2 },
  { label: 'Certifications', to: '/certifications', icon: BriefcaseBusiness },
  { label: 'Contact', to: '/contact', icon: Mail }
]
</script>

<template>
  <aside class="hidden w-56 shrink-0 lg:block" aria-label="Desktop sidebar">
    <div class="sticky top-24 space-y-5">
      <nav class="card content-card rounded-2xl p-3" aria-label="Portfolio sections">
        <p class="px-3 pb-2 pt-2 text-xs font-semibold uppercase tracking-[0.18em] text-base-content/45">Portfolio</p>
        <ul class="menu menu-sm gap-1 p-0">
          <li v-for="link in links" :key="link.to">
            <NuxtLink :to="link.to" :class="{ active: route.path === link.to }">
              <component :is="link.icon" :size="17" aria-hidden="true" />
              {{ link.label }}
            </NuxtLink>
          </li>
        </ul>
      </nav>

      <div class="card content-card rounded-2xl">
        <div class="card-body gap-3 p-5">
          <p class="text-sm font-semibold text-base-content">Let’s connect</p>
          <p class="text-xs leading-5 text-base-content/60">Open to opportunities and collaborations.</p>
          <NuxtLink to="/contact" class="link link-primary inline-flex items-center gap-1 text-sm font-medium no-underline">
            Get in touch <ArrowUpRight :size="15" aria-hidden="true" />
          </NuxtLink>
        </div>
      </div>
    </div>
  </aside>
</template>
