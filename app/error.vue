<script setup lang="ts">
import { ArrowLeft, CircleAlert, Home } from '@lucide/vue'

const props = defineProps<{
  error: {
    statusCode: number
    statusMessage?: string
  }
}>()

const isNotFound = computed(() => props.error.statusCode === 404)

useHead({ title: () => isNotFound.value ? 'Page Not Found | John Kendrick Cabunilas' : 'Something Went Wrong | John Kendrick Cabunilas' })
useSeoMeta({
  description: 'The requested page could not be found in John Kendrick Cabunilas’s portfolio.',
  robots: 'noindex, nofollow'
})

function goHome() {
  clearError({ redirect: '/' })
}
</script>

<template>
  <div class="min-h-screen bg-base-100 px-4 py-24 text-base-content">
    <main class="mx-auto flex min-h-[65vh] max-w-3xl flex-col items-center justify-center text-center">
      <div class="grid size-16 place-items-center rounded-2xl bg-primary/10 text-primary">
        <CircleAlert :size="34" aria-hidden="true" />
      </div>
      <p class="mt-6 text-sm font-semibold uppercase tracking-[0.2em] text-primary">
        {{ isNotFound ? '404 · Page not found' : `Error ${error.statusCode}` }}
      </p>
      <h1 class="mt-3 text-3xl font-bold sm:text-5xl">
        {{ isNotFound ? 'This page wandered off.' : 'Something went wrong.' }}
      </h1>
      <p class="mt-4 max-w-lg leading-7 text-base-content/65">
        {{ isNotFound ? 'The page you’re looking for doesn’t exist or may have moved. Let’s get you back to the portfolio.' : 'Please return to the homepage and try again.' }}
      </p>
      <div class="mt-8 flex flex-wrap justify-center gap-3">
        <button type="button" class="btn btn-primary" @click="goHome">
          <Home :size="17" aria-hidden="true" /> Back to home
        </button>
        <button type="button" class="btn btn-outline" @click="$router.back()">
          <ArrowLeft :size="17" aria-hidden="true" /> Go back
        </button>
      </div>
    </main>
  </div>
</template>
