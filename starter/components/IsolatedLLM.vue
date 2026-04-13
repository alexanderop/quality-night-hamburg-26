<template>
  <RoughSvg :width="920" :height="400" :padding="16" :roughness="1.6" :seed="11">
    <!-- Isolation bubble -->
    <RoughRect :x="30" :y="20" :width="860" :height="270" variant="muted" fill-style="dashed" :stroke-width="1" />
    <RoughText :x="460" :y="46" variant="subtitle">isolierte Blase — kein Zugriff nach außen</RoughText>

    <!-- USER icon: head + body -->
    <RoughCircle :x="130" :y="120" :diameter="40" variant="muted" fill-style="hachure" />
    <RoughPath d="M 90 185 Q 90 150 130 150 Q 170 150 170 185" variant="muted" :stroke-width="2" />
    <RoughText :x="130" :y="220" variant="label">USER</RoughText>
    <RoughText :x="130" :y="243" variant="subtitle">Frage</RoughText>

    <!-- LLM icon: brain = two lobes + center fold -->
    <RoughCircle :x="460" :y="150" :diameter="160" variant="default" fill-style="hachure" />
    <RoughPath
      d="M 395 135 C 395 100 440 95 460 125 C 480 95 525 100 525 135 C 545 155 525 190 495 190 C 485 200 435 200 425 190 C 395 190 375 155 395 135 Z"
      variant="default"
      :stroke-width="2"
    />
    <RoughPath d="M 460 118 L 460 195" variant="default" :stroke-width="1.5" />
    <RoughPath d="M 415 140 Q 430 150 420 165 M 500 140 Q 485 150 495 165" variant="default" :stroke-width="1.2" />
    <RoughText :x="460" :y="220" variant="label">LLM</RoughText>
    <RoughText :x="460" :y="243" variant="subtitle">denkt nach · Trainingsdaten</RoughText>

    <!-- OUTPUT icon: speech bubble with tail pointing left toward LLM -->
    <RoughPath
      d="M 760 95 L 850 95 L 850 165 L 760 165 L 760 150 L 740 135 L 760 120 Z"
      variant="accent"
      fill-style="hachure"
      :stroke-width="2"
    />
    <RoughText :x="805" :y="135" variant="label">?!</RoughText>
    <RoughText :x="805" :y="220" variant="label">OUTPUT</RoughText>
    <RoughText :x="805" :y="243" variant="subtitle">Halluzination</RoughText>

    <!-- Arrows -->
    <RoughArrow :x1="175" :y1="150" :x2="375" :y2="150" />
    <RoughArrow :x1="545" :y1="150" :x2="735" :y2="135" />

    <!-- Globe (Web) -->
    <RoughCircle :x="180" :y="345" :diameter="44" variant="muted" fill-style="hachure" />
    <RoughLine :x1="158" :y1="345" :x2="202" :y2="345" variant="muted" :stroke-width="1.2" />
    <RoughEllipse :x="180" :y="345" :width="22" :height="44" variant="muted" />
    <RoughLine :x1="152" :y1="317" :x2="208" :y2="373" variant="accent" :stroke-width="3" />
    <RoughText :x="260" :y="350" variant="subtitle">kein Web</RoughText>

    <!-- Hammer (Tools) -->
    <RoughPath
      d="M 425 315 L 490 315 L 490 335 L 465 335 L 465 375 L 450 375 L 450 335 L 425 335 Z"
      variant="muted"
      fill-style="hachure"
      :stroke-width="1.5"
    />
    <RoughLine :x1="415" :y1="305" :x2="500" :y2="385" variant="accent" :stroke-width="3" />
    <RoughText :x="555" :y="350" variant="subtitle">keine Tools</RoughText>

    <!-- Clock (Echtzeit) -->
    <RoughCircle :x="720" :y="345" :diameter="44" variant="muted" fill-style="hachure" />
    <RoughLine :x1="720" :y1="345" :x2="720" :y2="327" variant="muted" :stroke-width="1.8" />
    <RoughLine :x1="720" :y1="345" :x2="735" :y2="352" variant="muted" :stroke-width="1.8" />
    <RoughLine :x1="720" :y1="325" :x2="720" :y2="330" variant="muted" />
    <RoughLine :x1="720" :y1="360" :x2="720" :y2="365" variant="muted" />
    <RoughLine :x1="700" :y1="345" :x2="705" :y2="345" variant="muted" />
    <RoughLine :x1="735" :y1="345" :x2="740" :y2="345" variant="muted" />
    <RoughLine :x1="695" :y1="320" :x2="745" :y2="370" variant="accent" :stroke-width="3" />
    <RoughText :x="810" :y="350" variant="subtitle">keine Echtzeit</RoughText>
  </RoughSvg>
</template>
