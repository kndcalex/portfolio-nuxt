<script setup lang="ts">
import type { IconDefinition } from '@fortawesome/fontawesome-svg-core'
import type { SimpleIcon } from 'simple-icons'

const props = withDefaults(defineProps<{
  icon: SimpleIcon | IconDefinition
  size?: number
  color?: string
}>(), {
  size: 24,
  color: undefined
})

function isSimpleIcon(icon: SimpleIcon | IconDefinition): icon is SimpleIcon {
  return 'path' in icon
}

const svg = computed(() => {
  if (isSimpleIcon(props.icon)) {
    return {
      viewBox: '0 0 24 24',
      paths: [props.icon.path],
      color: props.color ?? `#${props.icon.hex}`
    }
  }

  const [width, height, , , path] = props.icon.icon
  return {
    viewBox: `0 0 ${width} ${height}`,
    paths: Array.isArray(path) ? path : [path],
    color: props.color ?? 'currentColor'
  }
})
</script>

<template>
  <svg
    :width="size"
    :height="size"
    :viewBox="svg.viewBox"
    fill="currentColor"
    aria-hidden="true"
    focusable="false"
    :style="{ color: svg.color }"
  >
    <path v-for="(path, index) in svg.paths" :key="index" :d="path" />
  </svg>
</template>
