<template>
  <RoughSvg :width="880" :height="320" :padding="12" :roughness="1.5" :seed="17">
    <!-- USER -->
    <RoughCircle :x="70" :y="95" :diameter="36" variant="muted" fill-style="hachure" />
    <RoughPath d="M 35 155 Q 35 122 70 122 Q 105 122 105 155" variant="muted" :stroke-width="2" />
    <RoughText :x="70" :y="180" variant="label">USER</RoughText>

    <!-- LLM brain (center) -->
    <RoughCircle :x="430" :y="115" :diameter="140" variant="default" fill-style="hachure" />
    <RoughPath
      d="M 375 105 C 375 75 415 72 430 98 C 445 72 485 75 485 105 C 502 122 485 152 460 152 C 452 160 408 160 400 152 C 375 152 358 122 375 105 Z"
      variant="default"
      :stroke-width="2"
    />
    <RoughPath d="M 430 90 L 430 158" variant="default" :stroke-width="1.5" />
    <RoughText :x="430" :y="195" variant="label">LLM</RoughText>

    <!-- OUTPUT -->
    <g v-click="4">
      <RoughPath
        d="M 720 75 L 840 75 L 840 145 L 720 145 L 720 130 L 700 115 L 720 100 Z"
        variant="accent"
        fill-style="hachure"
        :stroke-width="2"
      />
      <RoughPath d="M 745 112 L 770 135 L 810 88" variant="accent" :stroke-width="3" />
      <RoughText :x="780" :y="180" variant="label">ANSWER</RoughText>
    </g>

    <!-- Arrow 1: USER → LLM -->
    <g v-click="1">
      <RoughArrow :x1="115" :y1="115" :x2="355" :y2="115" />
    </g>

    <!-- Arrow 2: LLM → Tools (down) -->
    <g v-click="2">
      <RoughArrow :x1="400" :y1="195" :x2="310" :y2="250" variant="accent" />
      <RoughText :x="320" :y="220" variant="subtitle">call</RoughText>
    </g>

    <!-- Arrow 3: Tools → LLM (observation back up) -->
    <g v-click="3">
      <RoughArrow :x1="580" :y1="250" :x2="470" :y2="195" variant="accent" />
      <RoughText :x="560" :y="220" variant="subtitle">observe</RoughText>
    </g>

    <!-- Tools row -->
    <!-- Globe (Web) -->
    <RoughCircle :x="200" :y="275" :diameter="38" variant="accent" fill-style="hachure" />
    <RoughLine :x1="181" :y1="275" :x2="219" :y2="275" variant="accent" :stroke-width="1.2" />
    <RoughEllipse :x="200" :y="275" :width="19" :height="38" variant="accent" />
    <RoughText :x="200" :y="315" variant="subtitle">Web-Suche</RoughText>

    <!-- Hammer -->
    <RoughPath
      d="M 405 258 L 465 258 L 465 276 L 442 276 L 442 308 L 428 308 L 428 276 L 405 276 Z"
      variant="accent"
      fill-style="hachure"
      :stroke-width="1.5"
    />
    <RoughText :x="435" :y="325" variant="subtitle">Tool-Call</RoughText>

    <!-- File / Data -->
    <RoughPath
      d="M 620 255 L 665 255 L 680 270 L 680 310 L 620 310 Z"
      variant="accent"
      fill-style="hachure"
      :stroke-width="1.5"
    />
    <RoughLine :x1="665" :y1="255" :x2="665" :y2="270" variant="accent" />
    <RoughLine :x1="665" :y1="270" :x2="680" :y2="270" variant="accent" />
    <RoughText :x="650" :y="325" variant="subtitle">Daten / API</RoughText>

    <!-- Arrow 4: LLM → OUTPUT -->
    <g v-click="4">
      <RoughArrow :x1="505" :y1="115" :x2="695" :y2="105" />
    </g>
  </RoughSvg>
</template>
