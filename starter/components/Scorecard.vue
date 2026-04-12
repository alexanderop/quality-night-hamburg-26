<template>
  <!-- Intro mode: all cards muted -->
  <template v-if="mode === 'intro'">
    <div class="grid grid-cols-3 gap-3 mt-6">
      <Card v-for="(piece, idx) in PIECES.slice(0, 3)" :key="piece.key" v-click="idx + 1" variant="muted" size="sm">
        <div class="flex flex-col items-center gap-2 text-center">
          <div class="text-2xl" style="color: rgba(255,107,237,0.5)">{{ piece.icon }}</div>
          <div class="text-sm font-semibold text-gray-300">{{ piece.label }}</div>
          <div class="text-xs text-gray-500 leading-tight">{{ getDescription(piece) }}</div>
        </div>
      </Card>
    </div>

    <div class="grid grid-cols-3 gap-3 mt-3">
      <Card v-for="(piece, idx) in PIECES.slice(3)" :key="piece.key" v-click="idx + 4" variant="muted" size="sm">
        <div class="flex flex-col items-center gap-2 text-center">
          <div class="text-2xl" style="color: rgba(255,107,237,0.5)">{{ piece.icon }}</div>
          <div class="text-sm font-semibold text-gray-300">{{ piece.label }}</div>
          <div class="text-xs text-gray-500 leading-tight">{{ getDescription(piece) }}</div>
        </div>
      </Card>
    </div>

    <slot />
  </template>

  <!-- Progress mode: achieved/pending split -->
  <template v-else>
    <!-- Achieved cards -->
    <div v-if="achievedPieces.length > 0 && !allAchieved" v-click="1" class="grid grid-cols-2 gap-3 mt-4">
      <Card v-for="piece in achievedPieces" :key="piece.key" variant="success" glow size="sm">
        <div class="flex items-center gap-2 text-emerald-400 font-bold text-sm">
          &#10003; {{ piece.label }}
        </div>
        <p class="text-xs text-gray-400 mt-1 pl-5">{{ getDescription(piece) }}</p>
      </Card>
    </div>

    <!-- All 6 achieved: compact grid -->
    <div v-if="allAchieved" v-click="1" class="grid grid-cols-3 gap-3 mt-6">
      <Card v-for="piece in achievedPieces.slice(0, 3)" :key="piece.key" variant="success" glow size="sm">
        <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-sm">
          &#10003; {{ piece.label }}
        </div>
      </Card>
    </div>
    <div v-if="allAchieved" v-click="2" class="grid grid-cols-3 gap-3 mt-3">
      <Card v-for="piece in achievedPieces.slice(3)" :key="piece.key" variant="success" glow size="sm">
        <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-sm">
          &#10003; {{ piece.label }}
        </div>
      </Card>
    </div>

    <!-- Pending cards -->
    <div
      v-if="pendingPieces.length > 0"
      v-click="2"
      class="gap-2 mt-4"
      :style="{ display: 'grid', gridTemplateColumns: `repeat(${Math.min(pendingPieces.length, 4)}, minmax(0, 1fr))` }"
    >
      <Card v-for="piece in pendingPieces" :key="piece.key" variant="muted" dashed dimmed size="sm">
        <div class="flex items-center justify-center gap-1 text-sm">
          &#9675; {{ piece.label }}?
        </div>
      </Card>
    </div>

    <!-- Summary -->
    <div v-if="showSummary" v-click="3" class="text-center text-sm text-gray-500 tracking-wide" :class="allAchieved ? 'mt-6' : 'mt-8'">
      <span class="text-emerald-400 font-bold">{{ score }}</span> / <span class="text-gray-400">6</span> pieces unlocked
    </div>

    <slot />
  </template>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import Card from './Card.vue'

type PieceKey = 'llm' | 'agent' | 'browser' | 'cli' | 'skill' | 'pipeline'

interface Piece {
  key: PieceKey
  label: string
  icon: string
  description: string
}

const PIECES: Piece[] = [
  { key: 'llm', label: 'LLM', icon: '🧠', description: 'The brain that understands intent' },
  { key: 'agent', label: 'Agent', icon: '🤖', description: 'The loop that thinks and acts' },
  { key: 'browser', label: 'Browser Tool', icon: '🌐', description: 'Playwright controls the browser' },
  { key: 'cli', label: 'CLI > MCP', icon: '⚡', description: 'Minimal context, maximum clarity' },
  { key: 'skill', label: 'Skill File', icon: '📋', description: 'The job description for your agent' },
  { key: 'pipeline', label: 'CI Pipeline', icon: '🔄', description: 'GitHub Actions ties it together' },
]

const props = withDefaults(defineProps<{
  achieved: PieceKey[]
  descriptions?: Partial<Record<PieceKey, string>>
  mode?: 'progress' | 'intro'
  showSummary?: boolean
}>(), {
  mode: 'progress',
  showSummary: true,
})

const achievedSet = computed(() => new Set(props.achieved))
const score = computed(() => props.achieved.length)
const allAchieved = computed(() => score.value === 6)

const achievedPieces = computed(() =>
  PIECES.filter(p => achievedSet.value.has(p.key))
)

const pendingPieces = computed(() =>
  PIECES.filter(p => !achievedSet.value.has(p.key))
)

function getDescription(piece: Piece): string {
  return props.descriptions?.[piece.key] ?? piece.description
}
</script>
