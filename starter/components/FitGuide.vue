<template>
  <div class="grid grid-cols-2 gap-6 mt-4">
    <div>
      <h3 class="font-bold text-lg mb-3 text-emerald-400">Great fit</h3>
      <div class="space-y-2">
        <Card v-for="(item, idx) in good" :key="item.title" v-click="idx + 1" variant="success" size="sm">
          <div class="font-semibold text-sm text-emerald-300">{{ item.title }}</div>
          <div class="text-xs text-gray-400 mt-1">{{ item.description }}</div>
        </Card>
      </div>
    </div>
    <div>
      <h3 class="font-bold text-lg mb-3 text-red-400">Not the right tool</h3>
      <div class="space-y-2">
        <Card v-for="(item, idx) in bad" :key="item.title" v-click="idx + good.length + 1" variant="muted" size="sm">
          <div class="font-semibold text-sm text-red-300">{{ item.title }}</div>
          <div class="text-xs text-gray-400 mt-1">{{ item.description }}</div>
        </Card>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Card from './Card.vue'

defineProps<{
  good: { title: string; description: string }[]
  bad: { title: string; description: string }[]
}>()
</script>
