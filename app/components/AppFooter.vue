<script setup lang="ts">
import { Code2, MoveUp, UsersRound } from '@lucide/vue'

const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer mt-14 flex flex-col items-center justify-between gap-4 border-t border-base-300 py-7 text-sm text-base-content/55 sm:flex-row">
    <p>© {{ year }} John Kendrick Cabunilas. Built with Nuxt.</p>
    <div class="flex items-center gap-4">
      <a
        href="https://www.linkedin.com/in/john-kendrick-58949b3a8"
        target="_blank"
        rel="noopener noreferrer"
        class="link-hover inline-flex items-center gap-2"
        aria-label="LinkedIn profile (opens in a new tab)"
      >
        <UsersRound :size="17" aria-hidden="true" /> LinkedIn
      </a>
      <a
        href="https://github.com/kndcalex"
        target="_blank"
        rel="noopener noreferrer"
        class="link-hover inline-flex items-center gap-2"
        aria-label="GitHub profile (opens in a new tab)"
      >
        <Code2 :size="17" aria-hidden="true" /> GitHub
      </a>
      <a href="#main-content" class="btn btn-ghost btn-circle btn-sm" aria-label="Back to top">
        <MoveUp :size="16" aria-hidden="true" />
      </a>
    </div>
  </footer>
</template>
