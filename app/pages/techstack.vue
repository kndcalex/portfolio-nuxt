<script setup lang="ts">
import { Braces, Code2, Database, GitBranch, Globe2, Smartphone, Terminal } from '@lucide/vue'

useHead({ title: 'Tech Stack | John Kendrick Alexander Cabunilas' })
useSeoMeta({
  description: 'Technologies and tools John Kendrick Cabunilas has learned, including HTML, CSS, Python, Java, C, PostgreSQL, Kotlin, Git, and GitHub.',
  ogTitle: 'Tech Stack | John Kendrick Alexander Cabunilas',
  ogDescription: 'Languages, databases, and developer tools I’m learning.',
  ogType: 'website',
  twitterCard: 'summary'
})

const technologies = [
  { name: 'HTML', icon: Globe2, category: 'Web' },
  { name: 'CSS', icon: Braces, category: 'Web' },
  { name: 'Python', icon: Terminal, category: 'Language' },
  { name: 'Java', icon: Code2, category: 'Language' },
  { name: 'C', icon: Code2, category: 'Language' },
  { name: 'PostgreSQL', icon: Database, category: 'Database' },
  { name: 'Kotlin', icon: Smartphone, category: 'Language' },
  { name: 'Git', icon: GitBranch, category: 'Tools' },
  { name: 'GitHub', icon: Code2, category: 'Tools' }
]
</script>

<template>
  <div class="space-y-8">
    <header>
      <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">Tools I use and learn</p>
      <h1 class="page-title mt-2 text-3xl font-bold sm:text-4xl">My Tech Stack</h1>
      <p class="mt-3 text-base-content/60">Technologies and tools I’ve learned so far.</p>
    </header>

    <section class="grid gap-4 sm:grid-cols-2 xl:grid-cols-3" aria-label="Technologies and tools">
      <article v-for="technology in technologies" :key="technology.name" class="card content-card rounded-2xl">
        <div class="card-body flex-row items-center gap-4 p-5">
          <div class="grid size-12 shrink-0 place-items-center rounded-xl bg-primary/10 text-primary">
            <component :is="technology.icon" :size="24" aria-hidden="true" />
          </div>
          <div>
            <h2 class="font-semibold">{{ technology.name }}</h2>
            <span class="badge badge-ghost badge-sm mt-1">{{ technology.category }}</span>
          </div>
        </div>
      </article>
    </section>

    <TechStackChart />
  </div>
</template>
