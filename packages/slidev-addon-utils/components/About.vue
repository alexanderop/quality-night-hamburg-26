<template>
  <div class="h-full flex flex-col px-4 py-6">
    <h1 class="text-4xl font-semibold mb-10">Über mich</h1>

    <div class="grid grid-cols-2 gap-12 items-center flex-1">
      <div class="flex flex-col items-center">
        <div class="rounded-full p-1 bg-gradient-to-br from-[#ff6bed] to-purple-600">
          <img
            class="w-60 h-60 rounded-full object-cover block"
            src="https://avatars.githubusercontent.com/u/33398393?v=4"
          />
        </div>
        <h2 class="mt-6 text-3xl font-semibold">Alex Opalic</h2>
        <div class="mt-2 flex gap-4 text-base opacity-70">
          <span>alexop.dev</span>
          <span>·</span>
          <span>@alexanderopalic</span>
        </div>
      </div>

      <div class="flex flex-col gap-3">
        <div
          v-for="item in items"
          :key="item.text"
          class="flex items-center gap-4 px-5 py-3 rounded-xl bg-white/5 border border-white/10 text-lg"
        >
          <component :is="item.icon" class="text-[#ff6bed] text-xl shrink-0" />
          <span v-html="item.text" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { h } from 'vue'

const icon = (cls: string) => () => h('div', { class: `${cls} w-5 h-5` })

const items = [
  { icon: icon('i-carbon-rocket'), text: '8 Jahre Software Entwickler' },
  { icon: icon('i-carbon-building'), text: 'Entwickler bei Otto Payments 🦞' },
  { icon: icon('i-carbon-location'), text: 'Bayern' },
  { icon: icon('i-carbon-pen'), text: 'Blogger auf alexop.dev' },
  { icon: icon('i-carbon-microphone'), text: 'Speaker' },
]
</script>
