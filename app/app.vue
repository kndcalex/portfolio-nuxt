<script setup lang="ts">
const route = useRoute()
const scrollProgress = ref(0)
const activeSection = ref('#home')
const sectionIds = ['home', 'about', 'stack', 'certifications', 'contact']

function updateScrollProgress() {
  const scrollableHeight = document.documentElement.scrollHeight - window.innerHeight
  scrollProgress.value = scrollableHeight > 0
    ? Math.min(100, Math.round((window.scrollY / scrollableHeight) * 100))
    : 0

  const activeBoundary = window.innerHeight * 0.3
  let currentSection = 'home'
  for (const id of sectionIds) {
    const section = document.getElementById(id)
    if (section && section.getBoundingClientRect().top <= activeBoundary) {
      currentSection = id
    }
  }
  activeSection.value = `#${currentSection}`
}

onMounted(() => {
  updateScrollProgress()
  window.addEventListener('scroll', updateScrollProgress, { passive: true })
  window.addEventListener('resize', updateScrollProgress)
})

watch(() => route.fullPath, async () => {
  await nextTick()
  updateScrollProgress()
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', updateScrollProgress)
  window.removeEventListener('resize', updateScrollProgress)
})
</script>

<template>
  <div class="min-h-screen bg-base-100 text-base-content">
    <NuxtRouteAnnouncer />
    <AppHeader :scroll-progress="scrollProgress" :active-section="activeSection" />
    <div class="mx-auto w-full max-w-7xl px-4 pb-10 pt-24 sm:px-6 lg:px-8">
      <main id="main-content" class="min-w-0">
        <NuxtPage />
        <AppFooter />
      </main>
    </div>
  </div>
</template>
