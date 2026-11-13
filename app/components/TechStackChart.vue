<script setup lang="ts">
import { BarChart } from 'echarts/charts'
import { AriaComponent, GridComponent, TooltipComponent } from 'echarts/components'
import { init, use } from 'echarts/core'
import type { ECharts, EChartsOption } from 'echarts/core'
import { CanvasRenderer } from 'echarts/renderers'

use([BarChart, AriaComponent, GridComponent, TooltipComponent, CanvasRenderer])

const chartElement = ref<HTMLDivElement | null>(null)
let chart: ECharts | undefined

const categories = [
  { name: 'Web', count: 2 },
  { name: 'Languages', count: 4 },
  { name: 'Database', count: 1 },
  { name: 'Tools', count: 2 }
]

onMounted(() => {
  if (!chartElement.value) return

  chart = init(chartElement.value, 'dark')
  const option: EChartsOption = {
    aria: { enabled: true },
    grid: { left: 18, right: 18, top: 24, bottom: 12, containLabel: true },
    tooltip: { trigger: 'axis' },
    xAxis: {
      type: 'category',
      data: categories.map(category => category.name),
      axisLabel: { color: '#a0a0a0' },
      axisLine: { lineStyle: { color: '#333333' } }
    },
    yAxis: {
      type: 'value',
      minInterval: 1,
      axisLabel: { color: '#a0a0a0' },
      splitLine: { lineStyle: { color: '#252525' } }
    },
    series: [{
      type: 'bar',
      data: categories.map(category => category.count),
      barMaxWidth: 48,
      itemStyle: { color: '#ff6b35', borderRadius: [6, 6, 0, 0] }
    }]
  }

  chart.setOption(option)
  window.addEventListener('resize', resizeChart)
})

function resizeChart() {
  chart?.resize()
}

onBeforeUnmount(() => {
  window.removeEventListener('resize', resizeChart)
  chart?.dispose()
  chart = undefined
})
</script>

<template>
  <section class="card content-card rounded-2xl" aria-labelledby="tech-stack-breakdown">
    <div class="card-body">
      <div>
        <h2 id="tech-stack-breakdown" class="text-lg font-semibold">Tech stack breakdown</h2>
        <p class="mt-1 text-sm text-base-content/60">Number of listed technologies in each category.</p>
      </div>
      <div
        ref="chartElement"
        class="h-64 w-full"
        role="img"
        aria-label="Bar chart: Web 2 technologies, Languages 4, Database 1, Tools 2."
      />
      <ul class="flex flex-wrap gap-2" aria-label="Chart data summary">
        <li v-for="category in categories" :key="category.name" class="badge badge-outline">
          {{ category.name }}: {{ category.count }}
        </li>
      </ul>
    </div>
  </section>
</template>
