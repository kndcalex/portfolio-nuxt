<script setup lang="ts">
import { Award, ExternalLink, X } from '@lucide/vue'

useHead({ title: 'Certifications | John Kendrick Alexander Cabunilas' })
useSeoMeta({
  description: 'View John Kendrick Cabunilas’s certifications in Python, networking, Microsoft Word, PowerPoint, and C Essentials.',
  ogTitle: 'Certifications | John Kendrick Alexander Cabunilas',
  ogDescription: 'Certification badges and credential details.',
  ogType: 'website',
  twitterCard: 'summary'
})

const certifications = [
  { name: 'Python Essentials', badge: '/Image/python1.png', detail: '/Image/python.jpg', verification: 'https://www.credly.com/badges/38293d50-a3e1-48ef-a6b7-41daf8eee8b7/public_url' },
  { name: 'Networking Basics', badge: '/Image/net1.png', detail: '/Image/networking.jpg', verification: 'https://www.credly.com/badges/236fccca-de28-4a36-acf3-ca12f4d3851e/public_url' },
  { name: 'Microsoft Word Specialist', badge: '/Image/word1.png', detail: '/Image/word.jpg', verification: 'https://www.credly.com/badges/00181945-af5d-44a3-95a6-f6ab2c98da00/public_url' },
  { name: 'Microsoft PowerPoint Specialist', badge: '/Image/ptt1.png', detail: '/Image/ppt.jpg', verification: 'https://www.credly.com/badges/e0878de7-cccf-4a02-9dbe-917e43a133a2/public_url' },
  { name: 'C Essentials', badge: '/Image/c1.png', detail: '/Image/C.jpg', verification: 'https://www.credly.com/badges/02460c1f-8ef3-492a-a2bb-ee4da765244b/public_url' }
]

const selectedCertification = ref<(typeof certifications)[number] | null>(null)

function closeModal() {
  selectedCertification.value = null
}

function handleKeydown(event: KeyboardEvent) {
  if (event.key === 'Escape') closeModal()
}

watch(selectedCertification, (certification) => {
  if (import.meta.client) {
    document.body.style.overflow = certification ? 'hidden' : ''
  }
})

onMounted(() => window.addEventListener('keydown', handleKeydown))
onBeforeUnmount(() => {
  window.removeEventListener('keydown', handleKeydown)
  document.body.style.overflow = ''
})
</script>

<template>
  <div class="space-y-8">
    <header>
      <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">Learning milestones</p>
      <h1 class="page-title mt-2 text-3xl font-bold sm:text-4xl">Certifications</h1>
      <p class="mt-3 text-base-content/60">Select a badge to view its certificate image, or open its verification page.</p>
    </header>

    <section class="grid gap-4 sm:grid-cols-2 xl:grid-cols-3" aria-label="Certification badges">
      <article v-for="certification in certifications" :key="certification.name" class="card content-card rounded-2xl">
        <div class="card-body items-center gap-4 p-5 text-center">
          <button
            type="button"
            class="grid size-36 place-items-center rounded-2xl border border-base-300 bg-base-100 p-4 transition hover:border-primary focus-visible:outline focus-visible:outline-2 focus-visible:outline-primary"
            :aria-label="`View ${certification.name} certificate`"
            @click="selectedCertification = certification"
          >
            <img :src="certification.badge" :alt="`${certification.name} badge`" width="144" height="144" class="max-h-full max-w-full object-contain">
          </button>
          <h2 class="min-h-12 font-semibold">{{ certification.name }}</h2>
          <a
            :href="certification.verification"
            target="_blank"
            rel="noopener noreferrer"
            class="btn btn-outline btn-primary btn-sm"
          >
            Verify credential <ExternalLink :size="15" aria-hidden="true" />
          </a>
        </div>
      </article>
    </section>

    <dialog v-if="selectedCertification" open class="modal modal-open" aria-modal="true" aria-labelledby="certificate-title" @click.self="closeModal">
      <div class="modal-box max-h-[90vh] max-w-5xl overflow-y-auto border border-base-300 bg-base-200 p-3 sm:p-5">
        <div class="mb-3 flex items-center justify-between gap-4 px-2">
          <h2 id="certificate-title" class="font-semibold">{{ selectedCertification.name }}</h2>
          <button type="button" class="btn btn-circle btn-ghost btn-sm" aria-label="Close certificate" @click="closeModal">
            <X :size="20" aria-hidden="true" />
          </button>
        </div>
        <img :src="selectedCertification.detail" :alt="`${selectedCertification.name} certificate details`" class="mx-auto max-h-[75vh] w-auto max-w-full rounded-lg object-contain">
      </div>
      <form method="dialog" class="modal-backdrop" @submit.prevent="closeModal">
        <button aria-label="Close certificate dialog">close</button>
      </form>
    </dialog>

    <div class="alert border border-primary/20 bg-primary/5 text-base-content">
      <Award :size="20" class="text-primary" aria-hidden="true" />
      <span class="text-sm">Each credential links to its verification page when one is available.</span>
    </div>
  </div>
</template>
