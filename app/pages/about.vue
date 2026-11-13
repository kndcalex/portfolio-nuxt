<script setup lang="ts">
import { Compass, GraduationCap, Target, UserRound } from '@lucide/vue'

useHead({ title: 'About Me | John Kendrick Alexander Cabunilas' })
useSeoMeta({
  description: 'Learn about John Kendrick Alexander Cabunilas, his education, interests, and professional goals in technology and information systems.',
  ogTitle: 'About Me | John Kendrick Alexander Cabunilas',
  ogDescription: 'Background, education, interests, and goals in technology.',
  ogType: 'profile',
  twitterCard: 'summary'
})
</script>

<template>
  <div class="space-y-7">
    <header class="mb-8">
      <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">A little about me</p>
      <h1 class="page-title mt-2 text-3xl font-bold sm:text-4xl">About Me</h1>
      <p class="mt-3 text-base-content/60">Get to know who I am and what motivates me.</p>
    </header>

    <div class="grid gap-4">
      <ContentCard title="Who I Am" :icon="UserRound">
        <p>
          My name is John Kendrick Alexander Cabunilas, and I am currently a student with a strong passion for technology and information systems. I have always been fascinated by how computers and software work, which led me to pursue a path in IT. Beyond the screen, I love to travel and explore new places. I capture the beauty of nature through my camera and express myself through poetry. I believe that creativity and technology go hand in hand, and both fuel my drive to keep growing.
        </p>
      </ContentCard>

      <ContentCard title="My Education" :icon="GraduationCap">
        <p>
          I am currently pursuing my studies while actively building hands-on experience through various projects and certifications. My coursework has introduced me to programming, web development, and database management. I am committed to applying what I learn in class to real-world scenarios through practical projects and self-study.
        </p>
      </ContentCard>

      <ContentCard title="My Professional Goals" :icon="Target">
        <p>
          I dream of mastering complex systems and traveling freely. My journey in web development mirrors that vision: both are about building something reliable, whether it is a company’s digital infrastructure or my own platform for sharing travels, photography, and poetry with the world.
        </p>
      </ContentCard>

      <div class="alert border border-primary/20 bg-primary/5 text-base-content">
        <Compass :size="20" class="text-primary" aria-hidden="true" />
        <span class="text-sm">Curiosity, creativity, and continuous learning guide the work I do.</span>
      </div>
    </div>
  </div>
</template>
