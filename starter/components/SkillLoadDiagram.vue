<template>
  <RoughSvg :width="880" :height="340" :padding="14" :roughness="1.5" :seed="42">
    <!-- Stage 1: System Prompt (Metadata) -->
    <RoughRect :x="20" :y="80" :width="240" :height="120" variant="default" fill-style="hachure" :stroke-width="1.5" />
    <RoughText :x="140" :y="60" variant="label">1 · Startup</RoughText>
    <RoughText :x="140" :y="115" variant="label">System Prompt</RoughText>
    <RoughText :x="140" :y="140" variant="subtitle">name + description</RoughText>
    <RoughText :x="140" :y="162" variant="subtitle">(aller Skills)</RoughText>
    <RoughText :x="140" :y="225" variant="subtitle">~tiny · immer geladen</RoughText>

    <!-- Stage 2: SKILL.md Body -->
    <g v-click="1">
      <RoughArrow :x1="265" :y1="140" :x2="315" :y2="140" variant="accent" />
      <RoughText :x="290" :y="125" variant="subtitle">/invoke</RoughText>

      <RoughRect :x="320" :y="80" :width="240" :height="120" variant="accent" fill-style="hachure" :stroke-width="1.5" />
      <RoughText :x="440" :y="60" variant="label">2 · Invoke</RoughText>
      <RoughText :x="440" :y="115" variant="label">SKILL.md Body</RoughText>
      <RoughText :x="440" :y="140" variant="subtitle">Markdown als Message</RoughText>
      <RoughText :x="440" :y="162" variant="subtitle">in Conversation</RoughText>
      <RoughText :x="440" :y="225" variant="subtitle">full body · stays in ctx</RoughText>
    </g>

    <!-- Stage 3: Scripts / Supporting Files -->
    <g v-click="2">
      <RoughArrow :x1="565" :y1="140" :x2="615" :y2="140" variant="accent" />
      <RoughText :x="590" :y="125" variant="subtitle">on demand</RoughText>

      <RoughRect :x="620" :y="80" :width="240" :height="120" variant="muted" fill-style="hachure" :stroke-width="1.5" />
      <RoughText :x="740" :y="60" variant="label">3 · Execute</RoughText>
      <RoughText :x="740" :y="115" variant="label">Scripts / Files</RoughText>
      <RoughText :x="740" :y="140" variant="subtitle">Code läuft extern</RoughText>
      <RoughText :x="740" :y="162" variant="subtitle">nur Output → ctx</RoughText>
      <RoughText :x="740" :y="225" variant="subtitle">output only</RoughText>
    </g>

    <!-- Footer hint -->
    <g v-click="3">
      <RoughText :x="440" :y="285" variant="label">Progressive Disclosure</RoughText>
      <RoughText :x="440" :y="308" variant="subtitle">hunderte Skills → kein Context-Overhead</RoughText>
    </g>
  </RoughSvg>
</template>
