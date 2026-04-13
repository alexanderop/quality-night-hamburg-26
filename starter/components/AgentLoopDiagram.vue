<template>
  <RoughSvg :width="880" :height="340" :padding="14" :roughness="1.5" :seed="23">
    <!-- Node 1: User / Task (top-left) -->
    <RoughRect :x="40" :y="30" :width="220" :height="70" variant="muted" fill-style="hachure" :stroke-width="1.5" />
    <RoughText :x="150" :y="60" variant="label">1 · User / Task</RoughText>
    <RoughText :x="150" :y="84" variant="subtitle">„mach mir X"</RoughText>

    <!-- Node 2: LLM (top-right) -->
    <RoughRect :x="620" :y="30" :width="220" :height="70" variant="default" fill-style="hachure" :stroke-width="1.5" />
    <RoughText :x="730" :y="60" variant="label">2 · LLM plant</RoughText>
    <RoughText :x="730" :y="84" variant="subtitle">„ruf Tool X mit Y auf"</RoughText>

    <!-- Node 3: Tool (bottom-right) -->
    <RoughRect :x="620" :y="220" :width="220" :height="70" variant="accent" fill-style="hachure" :stroke-width="1.5" />
    <RoughText :x="730" :y="250" variant="label">3 · Tool läuft</RoughText>
    <RoughText :x="730" :y="274" variant="subtitle">Ergebnis → LLM</RoughText>

    <!-- Node 4: Done? (bottom-left) -->
    <RoughPath
      d="M 150 205 L 275 260 L 150 315 L 25 260 Z"
      variant="default"
      fill-style="hachure"
      :stroke-width="1.5"
    />
    <RoughText :x="150" :y="255" variant="label">4 · fertig?</RoughText>
    <RoughText :x="150" :y="278" variant="subtitle">ja / nein</RoughText>

    <!-- Arrow 1: User/Task → LLM -->
    <g v-click="1">
      <RoughArrow :x1="265" :y1="65" :x2="615" :y2="65" />
    </g>

    <!-- Arrow 2: LLM → Tool (down right side) -->
    <g v-click="2">
      <RoughArrow :x1="730" :y1="105" :x2="730" :y2="215" variant="accent" />
    </g>

    <!-- Arrow 3: Tool → Fertig? -->
    <g v-click="3">
      <RoughArrow :x1="615" :y1="255" :x2="280" :y2="260" variant="accent" />
    </g>

    <!-- Arrow 4a: nein → zurück zu LLM (loop back up) -->
    <g v-click="4">
      <RoughPath d="M 150 200 C 150 140 380 140 620 70" variant="accent" :stroke-width="2" />
      <RoughArrow :x1="605" :y1="74" :x2="618" :y2="68" variant="accent" />
      <RoughText :x="370" :y="150" variant="subtitle">nein → loop</RoughText>
    </g>

    <!-- Arrow 4b: ja → stop -->
    <g v-click="4">
      <RoughArrow :x1="30" :y1="260" :x2="-10" :y2="260" variant="default" />
      <RoughText :x="-30" :y="248" variant="label">ja</RoughText>
      <RoughText :x="-30" :y="272" variant="subtitle">stop</RoughText>
    </g>
  </RoughSvg>
</template>
