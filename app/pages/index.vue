<script setup lang="ts">
import { faLinkedinIn } from '@fortawesome/free-brands-svg-icons'
import {
  siGit,
  siGithub,
  siHtml5,
  siKotlin
} from 'simple-icons'
import {
  ArrowRight,
  Award,
  BriefcaseBusiness,
  Code2,
  Compass,
  ExternalLink,
  GraduationCap,
  Target,
  UserRound,
  X
} from '@lucide/vue'

useHead({ title: 'John Kendrick Alexander Cabunilas | Portfolio' })
useSeoMeta({
  description: 'Explore the portfolio of John Kendrick Alexander Cabunilas, an IT student passionate about technology, networking, and building useful digital experiences.',
  ogTitle: 'John Kendrick Alexander Cabunilas | Portfolio',
  ogDescription: 'A portfolio focused on technology, information systems, and continuous learning.',
  ogType: 'website',
  twitterCard: 'summary'
})

const technologies = [
  { name: 'HTML', icon: siHtml5, logo: null, category: 'Web' },
  { name: 'CSS', icon: null, logo: '/Image/css3-logo.svg', category: 'Web' },
  { name: 'JavaScript', icon: null, logo: '/Image/javascript-logo.svg', category: 'Language' },
  { name: 'Python', icon: null, logo: '/Image/python-logo.svg', category: 'Language' },
  { name: 'Java', icon: null, logo: '/Image/java-logo.svg', category: 'Language' },
  { name: 'C', icon: null, logo: '/Image/c-logo.svg', category: 'Language' },
  { name: 'PostgreSQL', icon: null, logo: '/Image/postgresql-logo.svg', category: 'Database' },
  { name: 'Kotlin', icon: siKotlin, logo: null, category: 'Language' },
  { name: 'Git', icon: siGit, logo: null, category: 'Tools' },
  { name: 'GitHub', icon: siGithub, logo: null, category: 'Tools' }
]

const certifications = [
  { name: 'Python Essentials', badge: '/Image/python1.png', detail: '/Image/Certificates/python-essentials.jpg', verification: 'https://www.credly.com/badges/38293d50-a3e1-48ef-a6b7-41daf8eee8b7/public_url' },
  { name: 'Networking Basics', badge: '/Image/net1.png', detail: '/Image/Certificates/networking-basics.jpg', verification: 'https://www.credly.com/badges/236fccca-de28-4a36-acf3-ca12f4d3851e/public_url' },
  { name: 'Microsoft Word Associate', badge: '/Image/word1.png', detail: '/Image/Certificates/word-associate.jpg', verification: 'https://www.credly.com/badges/e0878de7-cccf-4a02-9dbe-917e43a133a2/public_url' },
  { name: 'Microsoft PowerPoint Associate', badge: '/Image/ptt1.png', detail: '/Image/Certificates/powerpoint-associate.jpg', verification: 'https://www.credly.com/badges/e0878de7-cccf-4a02-9dbe-917e43a133a2/public_url' },
  { name: 'C Essentials', badge: '/Image/c1.png', detail: '/Image/Certificates/c-essentials.jpg', verification: 'https://www.credly.com/badges/02460c1f-8ef3-492a-a2bb-ee4da765244b/public_url' },
  { name: 'MongoDB Overview: Core Concepts and Architecture', badge: '/Image/Certificates/mongodb-overview-badge.jpg', detail: '/Image/Certificates/mongodb-overview-certificate.jpg', verification: 'https://www.credly.com/badges/8d32500f-247d-43ca-a9a9-92feb2847bb2' },
  { name: 'MongoDB CRUD Operations', badge: '/Image/Certificates/mongodb-crud-badge.jpg', detail: '/Image/Certificates/mongodb-crud-certificate.jpg', verification: 'https://www.credly.com/badges/c8469a15-3cf3-4a9b-b808-866b2d50df0f' }
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
  <div class="mx-auto max-w-4xl space-y-16">
    <section id="home" class="hero min-h-[26rem] scroll-mt-24 overflow-hidden rounded-3xl border border-base-300 bg-base-200 px-5 py-12 text-center sm:px-10">
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
            <a href="#about" class="btn btn-primary">
              About me <UserRound :size="17" aria-hidden="true" />
            </a>
            <a href="#stack" class="btn btn-outline btn-primary">
              Explore my tech stack <ArrowRight :size="17" aria-hidden="true" />
            </a>
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="scroll-mt-24 space-y-7" aria-labelledby="about-heading">
      <header class="mb-8">
        <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">A little about me</p>
        <h2 id="about-heading" class="page-title mt-2 text-3xl font-bold sm:text-4xl">About Me</h2>
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
    </section>

    <section id="stack" class="scroll-mt-24 space-y-8" aria-labelledby="stack-heading">
      <header>
        <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">Tools I use and learn</p>
        <h2 id="stack-heading" class="page-title mt-2 text-3xl font-bold sm:text-4xl">My Tech Stack</h2>
        <p class="mt-3 text-base-content/60">Technologies and tools I’ve learned so far.</p>
      </header>

      <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3" aria-label="Technologies and tools">
        <article v-for="technology in technologies" :key="technology.name" class="card content-card rounded-2xl">
          <div class="card-body flex-row items-center gap-4 p-5">
            <div class="grid size-12 shrink-0 place-items-center rounded-xl bg-primary/10">
              <img v-if="technology.logo" :src="technology.logo" alt="" aria-hidden="true" class="size-6 object-contain">
              <BrandIcon
                v-else-if="technology.icon"
                :icon="technology.icon"
                :size="24"
                :color="technology.name === 'Java' ? '#f89820' : technology.name === 'GitHub' ? '#f0f0f0' : undefined"
              />
            </div>
            <div>
              <h3 class="font-semibold">{{ technology.name }}</h3>
              <span class="badge badge-ghost badge-sm mt-1">{{ technology.category }}</span>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="certifications" class="scroll-mt-24 space-y-8" aria-labelledby="certifications-heading">
      <header>
        <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">Learning milestones</p>
        <h2 id="certifications-heading" class="page-title mt-2 text-3xl font-bold sm:text-4xl">Certifications</h2>
        <p class="mt-3 text-base-content/60">Select a badge to view its certificate image, or open its verification page.</p>
      </header>

      <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3" aria-label="Certification badges">
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
            <h3 class="min-h-12 font-semibold">{{ certification.name }}</h3>
            <a
              v-if="certification.verification"
              :href="certification.verification"
              target="_blank"
              rel="noopener noreferrer"
              class="btn btn-outline btn-primary btn-sm"
            >
              Verify credential <ExternalLink :size="15" aria-hidden="true" />
            </a>
          </div>
        </article>
      </div>

      <div class="alert border border-primary/20 bg-primary/5 text-base-content">
        <Award :size="20" class="text-primary" aria-hidden="true" />
        <span class="text-sm">Each credential links to its verification page when one is available.</span>
      </div>

      <dialog v-if="selectedCertification" open class="modal modal-open" aria-modal="true" aria-labelledby="certificate-title" @click.self="closeModal">
        <div class="modal-box max-h-[90vh] max-w-5xl overflow-y-auto border border-base-300 bg-base-200 p-3 sm:p-5">
          <div class="mb-3 flex items-center justify-between gap-4 px-2">
            <h3 id="certificate-title" class="font-semibold">{{ selectedCertification.name }}</h3>
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
    </section>

    <section id="contact" class="scroll-mt-24 space-y-8" aria-labelledby="contact-heading">
      <header>
        <p class="text-xs font-semibold uppercase tracking-[0.2em] text-primary">Say hello</p>
        <h2 id="contact-heading" class="page-title mt-2 text-3xl font-bold sm:text-4xl">Get In Touch</h2>
        <p class="mt-3 text-base-content/60">Let’s connect and collaborate.</p>
      </header>

      <div class="grid gap-4 sm:grid-cols-2" aria-label="Social profiles">
        <a
          href="https://www.linkedin.com/in/john-kendrick-58949b3a8"
          target="_blank"
          rel="noopener noreferrer"
          class="card content-card rounded-2xl no-underline"
        >
          <div class="card-body">
            <BrandIcon :icon="faLinkedinIn" :size="30" color="#0a66c2" />
            <h3 class="card-title mt-2">LinkedIn</h3>
            <p class="text-sm text-base-content/60">Connect with me professionally.</p>
            <span class="link link-primary mt-2 inline-flex items-center gap-1 text-sm">Visit profile <ExternalLink :size="15" aria-hidden="true" /></span>
          </div>
        </a>
        <a
          href="https://github.com/kndcalex"
          target="_blank"
          rel="noopener noreferrer"
          class="card content-card rounded-2xl no-underline"
        >
          <div class="card-body">
            <BrandIcon :icon="siGithub" :size="30" color="#f0f0f0" />
            <h3 class="card-title mt-2">GitHub</h3>
            <p class="text-sm text-base-content/60">Explore my projects and code.</p>
            <span class="link link-primary mt-2 inline-flex items-center gap-1 text-sm">View projects <ExternalLink :size="15" aria-hidden="true" /></span>
          </div>
        </a>
      </div>
    </section>
  </div>
</template>
