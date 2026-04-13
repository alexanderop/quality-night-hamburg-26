<template>
  <RoughSvg :width="900" :height="420" :padding="16" :roughness="1.5" :seed="29">
    <!-- Node 1 -->
    <RoughRect :x="55" :y="55" :width="240" :height="92" variant="muted" fill-style="hachure" :stroke-width="1.5" />
    <RoughText :x="175" :y="86" variant="label">1 · Dev schreibt Code</RoughText>
    <RoughText :x="175" :y="112" variant="subtitle">Feature, Diff, Commit</RoughText>

    <!-- Arrow 1: Dev → Claude #1 -->
    <g v-click="1">
      <RoughArrow :x1="300" :y1="100" :x2="600" :y2="100" />
    </g>

    <!-- Node 2 -->
    <g v-click="1">
      <RoughRect :x="605" :y="55" :width="240" :height="92" variant="default" fill-style="hachure" :stroke-width="1.5" />
      <RoughText :x="725" :y="86" variant="label">2 · Claude #1 lokal</RoughText>
      <RoughText :x="725" :y="112" variant="subtitle">`/pr` schreibt den Testplan</RoughText>
    </g>

    <!-- Arrow 2: Claude #1 → PR-Template -->
    <g v-click="2">
      <RoughArrow :x1="725" :y1="152" :x2="725" :y2="265" variant="accent" />
    </g>

    <!-- Node 3 -->
    <g v-click="2">
      <RoughRect :x="605" :y="270" :width="240" :height="92" variant="accent" fill-style="hachure" :stroke-width="1.5" />
      <RoughText :x="725" :y="300" variant="label">3 · PR-Template = Vertrag</RoughText>
      <RoughText :x="725" :y="326" variant="subtitle">AC, QA Scope, Scenarios</RoughText>
    </g>

    <!-- Arrow 3: PR-Template → Claude #2 -->
    <g v-click="3">
      <RoughArrow :x1="600" :y1="315" :x2="300" :y2="315" variant="accent" />
    </g>

    <!-- Node 4 -->
    <g v-click="3">
      <RoughRect :x="55" :y="270" :width="240" :height="92" variant="default" fill-style="hachure" :stroke-width="1.5" />
      <RoughText :x="175" :y="300" variant="label">4 · Claude #2 in CI</RoughText>
      <RoughText :x="175" :y="326" variant="subtitle">liest Vertrag, testet Browser</RoughText>
    </g>

    <!-- Center result with converging arrows -->
    <g v-click="4">
      <RoughArrow :x1="605" :y1="210" :x2="545" :y2="210" variant="accent" />
      <RoughArrow :x1="295" :y1="210" :x2="355" :y2="210" variant="accent" />
      <RoughPath
        d="M 450 165 L 540 210 L 450 255 L 360 210 Z"
        variant="accent"
        fill-style="hachure"
        :stroke-width="1.5"
      />
      <RoughText :x="450" :y="204" variant="label">5 · Verdict</RoughText>
      <RoughText :x="450" :y="228" variant="subtitle">Comment + Merge Gate</RoughText>
    </g>

    <!-- Arrow 4: Claude #2 → Dev (close the loop) -->
    <g v-click="5">
      <RoughArrow :x1="175" :y1="265" :x2="175" :y2="152" />
    </g>

    <!-- Loop label -->
    <g v-click="5">
      <RoughPath d="M 110 30 C 250 -10 650 -10 790 30" variant="accent" :stroke-width="2" />
      <RoughText :x="450" :y="28" variant="subtitle">nächster PR → Loop startet neu</RoughText>
    </g>
  </RoughSvg>
</template>
