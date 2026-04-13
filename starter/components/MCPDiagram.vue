<template>
  <RoughSvg :width="880" :height="340" :padding="12" :roughness="1.5" :seed="23" style="max-height: 56vh; width: auto;">
    <!-- AGENT (left) -->
    <RoughCircle :x="90" :y="130" :diameter="50" variant="muted" fill-style="hachure" />
    <RoughPath d="M 45 200 Q 45 160 90 160 Q 135 160 135 200" variant="muted" :stroke-width="2" />
    <RoughText :x="90" :y="230" variant="label">AGENT</RoughText>
    <RoughText :x="90" :y="250" variant="subtitle">(Claude Code)</RoughText>

    <!-- MCP SERVER (center) -->
    <RoughPath
      d="M 340 75 L 540 75 L 540 195 L 340 195 Z"
      variant="default"
      fill-style="hachure"
      :stroke-width="2"
    />
    <RoughLine :x1="340" :y1="110" :x2="540" :y2="110" variant="default" />
    <RoughCircle :x="360" :y="92" :diameter="8" variant="accent" fill-style="solid" />
    <RoughCircle :x="378" :y="92" :diameter="8" variant="accent" fill-style="solid" />
    <RoughCircle :x="396" :y="92" :diameter="8" variant="accent" fill-style="solid" />
    <RoughText :x="440" :y="145" variant="label">MCP SERVER</RoughText>
    <RoughText :x="440" :y="170" variant="subtitle">JSON-RPC</RoughText>
    <RoughText :x="440" :y="215" variant="subtitle">Playwright MCP</RoughText>

    <!-- BROWSER (right) -->
    <RoughPath
      d="M 720 80 L 850 80 L 850 195 L 720 195 Z"
      variant="accent"
      fill-style="hachure"
      :stroke-width="2"
    />
    <RoughLine :x1="720" :y1="105" :x2="850" :y2="105" variant="accent" />
    <RoughCircle :x="735" :y="92" :diameter="6" variant="accent" fill-style="solid" />
    <RoughCircle :x="750" :y="92" :diameter="6" variant="accent" fill-style="solid" />
    <RoughCircle :x="765" :y="92" :diameter="6" variant="accent" fill-style="solid" />
    <RoughText :x="785" :y="230" variant="label">BROWSER</RoughText>

    <!-- Click 1: Agent → MCP (tool call) -->
    <g v-click="1">
      <RoughArrow :x1="140" :y1="125" :x2="330" :y2="125" variant="accent" />
      <RoughText :x="235" :y="110" variant="subtitle">tool call</RoughText>
    </g>

    <!-- Click 2: MCP → Browser (execute) -->
    <g v-click="2">
      <RoughArrow :x1="545" :y1="110" :x2="715" :y2="110" variant="accent" />
      <RoughText :x="630" :y="95" variant="subtitle">execute</RoughText>
    </g>

    <!-- Click 3: Browser → MCP (snapshot/screenshot/DOM back) -->
    <g v-click="3">
      <RoughArrow :x1="715" :y1="165" :x2="545" :y2="165" variant="muted" />
      <RoughText :x="630" :y="185" variant="subtitle">snapshot + DOM + screenshot</RoughText>
    </g>

    <!-- Click 4: MCP → Agent (everything into context) -->
    <g v-click="4">
      <RoughArrow :x1="330" :y1="170" :x2="140" :y2="170" variant="muted" />
      <RoughText :x="235" :y="195" variant="subtitle">alles in den Context</RoughText>
    </g>

    <!-- Click 4: context blob visual on agent side -->
    <g v-click="4">
      <RoughPath
        d="M 30 265 L 160 265 L 160 310 L 30 310 Z"
        variant="muted"
        fill-style="hachure"
        :stroke-width="1.5"
      />
      <RoughText :x="95" :y="290" variant="subtitle">LLM Context ↑↑↑</RoughText>
    </g>
  </RoughSvg>
</template>
