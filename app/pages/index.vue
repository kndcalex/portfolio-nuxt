<script setup lang="ts">
import { ArrowRight, BriefcaseBusiness, Code2, UserRound } from '@lucide/vue'

useHead({ title: 'Home | John Kendrick Alexander Cabunilas' })
useSeoMeta({
  description: 'Explore the portfolio of John Kendrick Alexander Cabunilas, an IT student passionate about technology, networking, and building useful digital experiences.',
  ogTitle: 'John Kendrick Alexander Cabunilas | Portfolio',
  ogDescription: 'A portfolio focused on technology, information systems, and continuous learning.',
  ogType: 'website',
  twitterCard: 'summary'
})
</script>

<template>
  <div class="space-y-10">
    <section class="hero min-h-[26rem] overflow-hidden rounded-3xl border border-base-300 bg-base-200 px-5 py-12 text-center sm:px-10">
      <div class="hero-content flex-col gap-7">
        <div class="avatar">
          <div class="w-40 rounded-full ring ring-primary ring-offset-4 ring-offset-base-200 sm:w-52">
            <img src="/Image/profile.jpg" alt="John Kendrick Cabunilas" width="208" height="208">
          </div>
        </div>
        <div class="max-w-2xl">
          <p class="mb-3 text-xs font-semibold uppercase tracking-[0.24em] text-primary">Aspiring IT professional</p>
          <h1 class="page-title text-3xl font-bold leading-tight sm:text-5xl">Hi, I’m John Kendrick Alexander Cabunilas</h1>
          <p class="mx-auto mt-5 max-w-xl leading-7 text-base-content/65">
            Welcome to my portfolio. I’m passionate about technology, information systems, and building reliable digital experiences while continuing to learn and grow.
          </p>
          <div class="mt-7 flex flex-wrap justify-center gap-3">
            <NuxtLink to="/about" class="btn btn-primary">
              About me <UserRound :size="17" aria-hidden="true" />
            </NuxtLink>
            <NuxtLink to="/techstack" class="btn btn-outline btn-primary">
              Explore my tech stack <ArrowRight :size="17" aria-hidden="true" />
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <section aria-labelledby="highlights-heading">
      <div class="mb-5">
        <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">A quick introduction</p>
        <h2 id="highlights-heading" class="mt-2 text-2xl font-bold">Explore my portfolio</h2>
      </div>
      <div class="grid gap-4 md:grid-cols-2">
        <NuxtLink to="/techstack" class="card content-card rounded-2xl no-underline">
          <div class="card-body">
            <Code2 :size="24" class="text-primary" aria-hidden="true" />
            <h3 class="card-title mt-2">Technology & tools</h3>
            <p class="text-sm leading-6 text-base-content/60">See the languages, platforms, and tools I’m learning.</p>
          </div>
        </NuxtLink>
        <NuxtLink to="/certifications" class="card content-card rounded-2xl no-underline">
          <div class="card-body">
            <BriefcaseBusiness :size="24" class="text-primary" aria-hidden="true" />
            <h3 class="card-title mt-2">Certifications</h3>
            <p class="text-sm leading-6 text-base-content/60">Browse my completed certification badges and details.</p>
          </div>
        </NuxtLink>
      </div>
    </section>
  </div>
</template>
