<script setup lang="ts">
import { ArrowUpRight, Code2, Mail, UsersRound } from '@lucide/vue'

useHead({ title: 'Contact | John Kendrick Alexander Cabunilas' })
useSeoMeta({
  description: 'Get in touch with John Kendrick Cabunilas. Connect on LinkedIn or GitHub for opportunities and collaborations.',
  ogTitle: 'Contact | John Kendrick Alexander Cabunilas',
  ogDescription: 'Connect with John Kendrick Cabunilas on LinkedIn and GitHub.',
  ogType: 'website',
  twitterCard: 'summary'
})
</script>

<template>
  <div class="space-y-8">
    <header>
      <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">Say hello</p>
      <h1 class="page-title mt-2 text-3xl font-bold sm:text-4xl">Get In Touch</h1>
      <p class="mt-3 text-base-content/60">Let’s connect and collaborate.</p>
    </header>

    <section class="grid gap-4 sm:grid-cols-2" aria-label="Social profiles">
      <a
        href="https://www.linkedin.com/in/john-kendrick-58949b3a8"
        target="_blank"
        rel="noopener noreferrer"
        class="card content-card rounded-2xl no-underline"
      >
        <div class="card-body">
          <UsersRound :size="30" class="text-primary" aria-hidden="true" />
          <h2 class="card-title mt-2">LinkedIn</h2>
          <p class="text-sm text-base-content/60">Connect with me professionally.</p>
          <span class="link link-primary mt-2 inline-flex items-center gap-1 text-sm">Visit profile <ArrowUpRight :size="15" aria-hidden="true" /></span>
        </div>
      </a>
      <a
        href="https://github.com/kndcalex"
        target="_blank"
        rel="noopener noreferrer"
        class="card content-card rounded-2xl no-underline"
      >
        <div class="card-body">
          <Code2 :size="30" class="text-primary" aria-hidden="true" />
          <h2 class="card-title mt-2">GitHub</h2>
          <p class="text-sm text-base-content/60">Explore my projects and code.</p>
          <span class="link link-primary mt-2 inline-flex items-center gap-1 text-sm">View projects <ArrowUpRight :size="15" aria-hidden="true" /></span>
        </div>
      </a>
    </section>

    <div class="alert border border-primary/20 bg-primary/5 text-base-content">
      <Mail :size="20" class="text-primary" aria-hidden="true" />
      <span class="text-sm">Open to opportunities and collaborations.</span>
    </div>
  </div>
</template>
