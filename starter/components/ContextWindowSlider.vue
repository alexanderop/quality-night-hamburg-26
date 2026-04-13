<script setup lang="ts">
import { computed, ref } from 'vue'

const percent = ref(26)
const totalTokens = 200_000

const zone = computed(() => {
  if (percent.value < 40) return { label: 'Smart', color: '#22c55e', emoji: '🙂', desc: 'Smart Zone' }
  if (percent.value < 60) return { label: 'Optimal', color: '#eab308', emoji: '😐', desc: 'Optimal' }
  if (percent.value < 80) return { label: 'Degraded', color: '#f97316', emoji: '😟', desc: 'Degraded' }
  return { label: 'Critical', color: '#ef4444', emoji: '😰', desc: 'Critical' }
})

const usedTokens = computed(() => Math.round((percent.value / 100) * totalTokens).toLocaleString('de-DE'))
</script>

<template>
  <div class="cw-wrap">
    <div class="cw-zones">
      <div class="cw-zone cw-smart">Smart</div>
      <div class="cw-zone cw-optimal">Optimal</div>
      <div class="cw-zone cw-degraded">Degraded</div>
      <div class="cw-zone cw-critical">Critical</div>
      <div class="cw-marker" :style="{ left: percent + '%' }"></div>
    </div>

    <div class="cw-scale">
      <span>0%</span><span>40%</span><span>60%</span><span>80%</span><span>100%</span>
    </div>

    <div class="cw-display">
      <div class="cw-emoji" :style="{ borderColor: zone.color, color: zone.color }">{{ zone.emoji }}</div>
      <div class="cw-stats">
        <div class="cw-percent" :style="{ color: zone.color }">{{ percent }}%</div>
        <div class="cw-label" :style="{ color: zone.color }">{{ zone.desc }}</div>
        <div class="cw-tokens">{{ usedTokens }} / 200.000 Tokens</div>
      </div>
    </div>

    <div class="cw-slider-wrap">
      <div class="cw-slider-track"></div>
      <input type="range" min="0" max="100" v-model.number="percent" class="cw-slider" />
    </div>
  </div>
</template>

<style scoped>
.cw-wrap {
  border: 1.5px solid #ff6bed;
  border-radius: 12px;
  padding: 2rem 2.5rem;
  background: rgba(0, 0, 0, 0.2);
  font-family: 'Geist Mono', monospace;
}

.cw-zones {
  position: relative;
  display: grid;
  grid-template-columns: 40fr 20fr 20fr 20fr;
  height: 52px;
  border-radius: 6px;
  overflow: hidden;
}
.cw-zone {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  font-weight: 500;
}
.cw-smart    { background: rgba(34,197,94,0.18);  color: #22c55e; }
.cw-optimal  { background: rgba(234,179,8,0.18);  color: #eab308; }
.cw-degraded { background: rgba(249,115,22,0.18); color: #f97316; }
.cw-critical { background: rgba(239,68,68,0.18);  color: #ef4444; }

.cw-marker {
  position: absolute;
  top: -4px;
  bottom: -4px;
  width: 3px;
  background: #fff;
  box-shadow: 0 0 8px rgba(255,255,255,0.8);
  transform: translateX(-50%);
  transition: left 0.15s ease;
  pointer-events: none;
}

.cw-scale {
  display: flex;
  justify-content: space-between;
  margin-top: 0.4rem;
  font-size: 0.8rem;
  color: #888;
}
.cw-scale span:nth-child(2) { margin-left: 32%; }
.cw-scale span:nth-child(3) { margin-left: 8%; }
.cw-scale span:nth-child(4) { margin-left: 8%; }

.cw-display {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  margin: 2rem 0 1.5rem;
}
.cw-emoji {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  border: 2px solid;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.6rem;
}
.cw-stats { text-align: left; }
.cw-percent { font-size: 3rem; font-weight: 700; line-height: 1; }
.cw-label { font-size: 1rem; margin-top: 0.2rem; }
.cw-tokens { font-size: 0.8rem; color: #888; margin-top: 0.3rem; }

.cw-slider-wrap {
  position: relative;
  height: 18px;
  margin-top: 1rem;
}
.cw-slider-track {
  position: absolute;
  inset: 4px 0;
  border-radius: 999px;
  background: linear-gradient(
    to right,
    #22c55e 0%, #22c55e 40%,
    #eab308 40%, #eab308 60%,
    #f97316 60%, #f97316 80%,
    #ef4444 80%, #ef4444 100%
  );
}
.cw-slider {
  position: absolute;
  inset: 0;
  width: 100%;
  -webkit-appearance: none;
  appearance: none;
  background: transparent;
  cursor: pointer;
}
.cw-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 22px;
  height: 22px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid #000;
  cursor: pointer;
  box-shadow: 0 2px 6px rgba(0,0,0,0.4);
}
.cw-slider::-moz-range-thumb {
  width: 22px;
  height: 22px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid #000;
  cursor: pointer;
}
</style>
