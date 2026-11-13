<script setup lang="ts">
import type { Component } from 'vue'

defineProps<{
  title: string
  icon?: Component
}>()
</script>

<template>
  <section class="card content-card rounded-2xl">
    <div class="card-body gap-4 p-5 sm:p-7">
      <h2 class="flex items-center gap-3 text-lg font-semibold text-primary">
        <component :is="icon" v-if="icon" :size="20" aria-hidden="true" />
        {{ title }}
      </h2>
      <div class="leading-7 text-base-content/70">
        <slot />
      </div>
    </div>
  </section>
</template>
