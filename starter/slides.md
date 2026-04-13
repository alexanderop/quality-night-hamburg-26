---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: 'Einen KI-QA-Engineer bauen mit Claude Code & Playwright'
transition: slide-left
mdc: true
drawings:
  persist: false
info: |
  ## Einen KI-QA-Engineer bauen mit Claude Code & Playwright

  Von Alexander Opalic — Quality Night Hamburg 2026
hideFooter: true
layout: image
image: /quality-night-hamburg-2026.jpeg
backgroundSize: contain
---

---
layout: center
class: text-center
---

# Einen KI-QA-Engineer bauen

<div class="mt-10 text-3xl opacity-80 whitespace-nowrap">
  mit Claude Code und
</div>

<div class="mt-4 text-5xl font-bold whitespace-nowrap h-16 flex items-center justify-center">
  <v-switch>
    <template #1><span>Playwright MCP</span></template>
    <template #2><span v-mark.red.strike-through>Playwright MCP</span></template>
    <template #3>
      <span
        v-motion
        :initial="{ y: 30, opacity: 0 }"
        :enter="{ y: 0, opacity: 1, transition: { duration: 500 } }"
        class="text-[#ff6bed]"
      >agent-browser</span>
    </template>
  </v-switch>
</div>

---
layout: image
image: /ai-buzzwords.png
backgroundSize: contain
---

---
layout: statement
---

# Wie kann man KI<br/>sinnvoll im <span class="text-[#ff6bed]">QA-Bereich</span> einsetzen?

---
layout: statement
---

# Coden ist gelöst

<div class="mt-6 text-2xl opacity-80">Ich hab gefühlt seit 4 Monaten<br/>kaum noch selbst Code geschrieben.</div>

---
layout: image
image: /ryanDahl.png
backgroundSize: contain
---

---

# Die Software Factory

Du schreibst eine Spec. Der Agent baut. Du reviewst.

> "We're going to start to see the title of software engineer go away. It's just going to be **'builder'** or 'product manager'."
>
> — Boris Cherny, Creator of Claude Code

**Stripe Minions:** über **1.300 PRs pro Woche** — agent-geschrieben, human-reviewed.

---
layout: image
image: /stripe-minions.png
backgroundSize: contain
---

---
layout: image
image: /software-factory.png
backgroundSize: contain
---

---

# Die neuen Bottlenecks

Code ist schnell. Was rückt nach?

<div class="grid grid-cols-3 gap-6 mt-10 text-sm">
  <div class="border border-[#ff6bed] rounded px-4 py-5 bg-[#ff6bed]/10">
    <div class="text-xs uppercase tracking-wider opacity-60 mb-2">Bottleneck #1</div>
    <div class="text-xl font-bold mb-2">Business</div>
    <div class="opacity-80">Was bauen wir überhaupt? Was lohnt sich?</div>
  </div>
  <div class="border border-[#ff6bed] rounded px-4 py-5 bg-[#ff6bed]/10">
    <div class="text-xs uppercase tracking-wider opacity-60 mb-2">Bottleneck #2</div>
    <div class="text-xl font-bold mb-2">QA</div>
    <div class="opacity-80">Funktioniert das, was der Agent gebaut hat?</div>
  </div>
  <div class="border border-white/20 rounded px-4 py-5 bg-white/5">
    <div class="text-xs uppercase tracking-wider opacity-60 mb-2">Noch Bottleneck #3</div>
    <div class="text-xl font-bold mb-2">Code Review</div>
    <div class="opacity-80">Für jetzt. Aber wer weiß wie lange noch.</div>
  </div>
</div>

<div class="mt-10 text-center opacity-80">Das Tippen ist nicht mehr das Problem. Das <b>Prüfen</b> wird zum Engpass.</div>

---
layout: statement
---

# Heute: <span class="text-[#ff6bed]">QA</span>

<div class="mt-6 text-2xl opacity-80">Wenn AI den Code schreibt,<br/>muss QA mitwachsen — sonst landen Bugs in Production.</div>

---
layout: image-right
image: /manning-book.png
---

# Buch-Empfehlung

**Software Testing with Generative AI** — Mark Winteringham

Use-Cases aus dem Buch:

- 🧪 **Test-Daten generieren** — realistische Fixtures, auch via SQL-Seeds
- ✍️ **Tests & Boilerplate schreiben** lassen (Unit, Integration, E2E)
- 📄 **Page Objects aus HTML** generieren
- 🧭 **Test-Pläne aus Tickets** ableiten (RAG + Fine-Tuning)

<div class="text-xs opacity-60 mt-2">Mein Fazit: ⭐⭐⭐⭐ — top Einstieg, besonders Shift-Left-Testing & Prompt für Test-Daten-Generierung</div>
<div class="text-xs opacity-60 mt-1">manning.com/books/software-testing-with-generative-ai</div>

---
layout: statement
---

# Disclaimer

<div class="mt-6 text-2xl opacity-80">Vieles davon ist heute noch sehr experimentell.</div>
<div class="mt-4 text-2xl">Aber ich bin überzeugt: <span class="text-[#ff6bed]">dort geht die Reise hin.</span></div>

---

<About />

---

# LLM = Autocomplete auf Steroiden

<div class="text-center text-xl mb-4 opacity-90">
"Der Hund läuft über die ___"
</div>

<RoughSvg :width="700" :height="260" :padding="16" :roughness="1.4" :seed="11">
  <RoughRect :x="80"  :y="107" :width="140" :height="93" variant="accent" fill-style="hachure" />
  <RoughRect :x="280" :y="169" :width="140" :height="31" variant="default" fill-style="hachure" />
  <RoughRect :x="480" :y="187" :width="140" :height="13" variant="default" fill-style="hachure" />

  <RoughText :x="150" :y="90"  variant="label">62%</RoughText>
  <RoughText :x="350" :y="152" variant="label">21%</RoughText>
  <RoughText :x="550" :y="170" variant="label">9%</RoughText>

  <RoughText :x="150" :y="225" variant="subtitle">Straße</RoughText>
  <RoughText :x="350" :y="225" variant="subtitle">Wiese</RoughText>
  <RoughText :x="550" :y="225" variant="subtitle">Brücke</RoughText>

  <RoughLine :x1="40" :y1="200" :x2="660" :y2="200" />
</RoughSvg>

Das LLM würfelt nicht  es **gewichtet**. Jedes nächste Token ist eine Wahrscheinlichkeitsverteilung. Klingt nach "stochastischem Papagei" — viele sehen es genau so.

---

# Vom LLM zum Agent

<IsolatedLLM />

---

# Tools verändern alles

<div class="flex justify-center">
  <AgentDiagram />
</div>

<div v-click="5" class="text-sm opacity-90 mt-2">

**Agent** = LLM als "Hirn" + **Tools**, um eine Aufgabe **eigenständig** zu Ende zu bringen.

</div>

---
layout: image
image: /tiny-agent.png
backgroundSize: contain
---

---

# 🙋 Kurze Umfrage

Wer von euch hat schon mal benutzt…

- **Claude Code**?
- **OpenAI Codex CLI**?
- den **VS Code Copilot Agent**?

---

# Claude Code

Anthropic, Research Preview im **Februar 2025** — CLI-basierter Coding-Agent, heute der Standard für agentic Coding.

> "Claude Code is, with hindsight, poorly named. It's not purely a coding tool: it's a tool for **general computer automation**. It's best described as a **general agent**."
>
> — Simon Willison

**Default-Tools:** `Read`, `Write` / `Edit`, `Grep` / `Glob`, `Bash`

Allgemeiner Agent mit Tools — perfekt, um QA-Aufgaben zu automatisieren.

---

# Claude Code in Action

<div class="flex justify-center">
  <video src="/claudecode.mp4" controls muted loop class="rounded-lg max-h-[420px]" />
</div>

---
layout: image
image: /agent-tools.png
backgroundSize: contain
---

---

# Der ganze Trick in 4 Zeilen

<div class="flex justify-center">
  <AgentLoopDiagram />
</div>

<div v-click="5" class="text-sm opacity-90 mt-2">

Mehr ist ein Agent nicht. **LLM denkt, Tools handeln, Loop wiederholt.**

</div>

---

# Claude Code installieren

```bash
curl -fsSL https://claude.ai/install.sh | bash   # macOS/Linux (alt: brew install --cask claude-code)
claude           # startet den Agent im aktuellen Ordner – Login per Browser beim ersten Start
```

**Was du brauchst:**

- Einen **Anthropic-Account** – Claude Pro ab ~20 €/Monat deckt die meisten Use-Cases ab (Max ab ~100 $/Monat, oder API-Key Pay-as-you-go)
- Ein Terminal deiner Wahl

→ Nach 2 Minuten läuft der Agent auf deinem Rechner. Montag einfach ausprobieren.

---

<div class="flex justify-center items-center h-full">
  <div class="relative" style="width: 360px; height: 640px; background: #111; border: 8px solid #222; border-radius: 40px; box-shadow: 0 0 0 2px #333, 0 20px 60px rgba(0,0,0,0.6); padding: 10px;">
    <div class="absolute left-1/2 -translate-x-1/2 top-2 w-20 h-4 bg-black rounded-full z-10"></div>
    <iframe
      src="https://workout-tracker-ten-pi.vercel.app/"
      class="w-full h-full rounded-3xl bg-black phone-iframe"
      style="scrollbar-width: none;"
    ></iframe>
  </div>
</div>

<style>
.phone-iframe::-webkit-scrollbar { display: none; }
</style>

---
layout: statement
---

# Was macht einen guten QA-Engineer aus?

---

# Unsere Idee

Ein **QA-Agent**, der in **GitHub Actions** läuft und anhand der **PR-Beschreibung** prüft, ob die Implementierung wirklich umgesetzt wurde.

<v-clicks>

- liest die **PR-Description** als Auftrag
- findet selbstständig **Edge Cases**
- testet wie ein **guter QA-Engineer**

</v-clicks>

<v-click>

**Wie kommen wir dahin?**

</v-click>

<v-clicks>

1. Erst verstehen, wie wir den Agent **lokal** aufsetzen
2. Dann ab in die **GitHub Actions** Pipeline

</v-clicks>

---
layout: image
image: /qa-smoke-test-report.png
backgroundSize: contain
---

---

# Was Claude Code fehlt

Claude Code kann lesen, schreiben, suchen, Bash ausführen — aber es kann **keinen Browser bedienen**.

Genau das müssen wir ihm geben.

→ Wenn der Agent **einen echten Browser steuern** kann, kann er auch unsere App **wie ein QA-Engineer testen**: klicken, tippen, navigieren, validieren.

---

# Wie geben wir dem Agent Browser-Tools?

Zwei Wege, dem Agent neue Fähigkeiten zu geben:

- 🔌 **MCP** (Model Context Protocol)
- 💻 **CLI** — ein ganz normales Terminal-Tool

Schauen wir uns erst an, was MCP eigentlich ist.

---

# Was ist MCP?

<div class="text-sm opacity-90">

**Model Context Protocol** — Anthropic-Standard, damit Agents mit externen Tool-Servern reden. Server stellt Tools bereit, Agent ruft per JSON-RPC auf — **jede Antwort fließt direkt in den LLM-Kontext**.

</div>

<div class="flex justify-center mt-2">
  <MCPDiagram />
</div>

---

# Und CLI?

Kein Server. Kein Protokoll. Einfach ein Kommandozeilen-Tool, das der Agent über sein Bash-Tool aufruft.

```bash
agent-browser snapshot -i > snapshot.yml
agent-browser screenshot -o shot.png
```

- Output landet **auf der Festplatte** (oder als stdout)
- Der Agent entscheidet **selbst**, was er liest: `cat snapshot.yml`, `head -20 shot.meta.json`
- Nichts fließt automatisch in den Context

---

# Der Unterschied

**MCP pusht Daten in den Context. CLI lässt den Agent pullen.**

MCP pipet bei jedem Tool-Call alles zurück: Snapshot, Screenshot, DOM — auch wenn der Agent es gar nicht braucht.

| | MCP | CLI |
|---|---|---|
| Token-Verbrauch (gleiche Demo) | 114 K | **26.8 K** |
| Faktor | 1× | **~4× weniger** |

Coding-Agents wie Claude Code haben eh Filesystem + Bash → der MCP-Layer ist für Browser-Tools schlicht redundant.

<div class="text-xs opacity-60 mt-4">Quelle: Playwright CLI vs MCP — A New Tool for Your Coding Agent</div>

---

# Wo MCP trotzdem Sinn macht

CLI gewinnt dort, wo das Modell die Tools schon kennt: `git`, `docker`, `kubectl`, `bash`.

<v-click>

MCP gewinnt dort, wo es gar kein CLI gibt.

</v-click>

<v-clicks>

- **SaaS ohne CLI**: Figma, Notion, Linear, Salesforce, Workday
- **Multi-Tenant**: OAuth pro User, Zugriff einzeln widerrufbar
- **Enterprise Governance**: strukturierte Audit-Logs statt `bash history`

</v-clicks>

<v-click>

Für unseren QA-Agent bleibt CLI richtig. Für einen Agent, der Linear-Tickets zieht und Figma-Designs prüft, wäre es MCP.

</v-click>

---

# OpenClaw: nur CLIs, keine MCPs

**Peter Steinberger** (PSPDFKit, $100M Exit) baut mit **OpenClaw** einen persönlichen AI-Agent, der bewusst **kein MCP** unterstützt.

<v-clicks>

- ~10 eigene CLIs für OpenClaw gebaut, dafür von OpenAI abgeworben
- Sein Satz: *"MCP was a mistake. Bash is better."*
- Alles läuft über **Skills** (Markdown + CLI-Aufrufe)

</v-clicks>

<v-click>

Für Tools, die es nur als MCP gibt, hat er einen **Konverter** geschrieben: **MCP → CLI**. Jede MCP-Funktion wird zum normalen Command-Line-Aufruf, dynamisch, ohne Restart.

</v-click>

<v-click>

Dieselbe Idee wie bei uns: dem Agent die Tools geben, die auch Menschen benutzen.

</v-click>

<div class="text-xs opacity-60 mt-4">Quelle: steipete.me, oreateai.com/blog</div>

---

# Aber: ich nutze Playwright gar nicht

Stattdessen: **Agent Browser** (vercel-labs)

- Native **Rust CLI** für Browser-Automation
- Kein Node.js, kein Playwright-Runtime nötig
- Nutzt Chrome for Testing unter der Haube
- Pro Workspace eigener Browser (`.agent-browser/`)
- **Snapshot-and-ref Modell** — perfekt für Agents

---

# Snapshot-and-ref

```bash
agent-browser open https://workout-tracker-ten-pi.vercel.app
agent-browser snapshot -i        # interaktive Elemente mit refs
agent-browser click @e2          # per ref klicken
agent-browser fill @e3 "Squat"
agent-browser console            # JS-Errors auslesen
agent-browser screenshot
```

`snapshot -i` gibt einen Accessibility-Tree zurück, in dem **jedes Element eine ref wie `@e1` bekommt**. Keine harten Selektoren. Layout ändert sich? Egal — Claude liest den neuen Snapshot und arbeitet mit den neuen refs.

```bash
- link "zur Homepage" [ref=e1]
- searchbox "Wonach suchst du?" [ref=e2]
- button "Suche abschicken" [ref=e3]
```

---

<div class="flex justify-center">
  <img src="/otto-a11y-dom.png" class="rounded-lg max-h-[420px]" />
</div>

---

# Agent Browser in Action

<div class="flex justify-center">
  <video src="/userAgent.mp4" controls muted loop class="rounded-lg max-h-[480px]" />
</div>

---

# Snapshot Output

<div class="flex justify-center">
  <img src="/qa-smoke-test-report.png" class="rounded-lg max-h-[480px]" />
</div>

---

# Der Loop

<v-clicks>

1. `snapshot -i` → Claude sieht die Seite
2. Claude überlegt: "Ich teste die Navigation"
3. `click @e12`
4. `snapshot -i` → neue Seite
5. `console` → keine Errors
6. ✅ Test bestanden

</v-clicks>

---

# `claude -p` — der One-Shot Modus

Derselbe Claude Code, aber **ohne REPL**:

```bash
claude -p "deine aufgabe hier" --allowedTools "Bash(agent-browser*)"
```

`claude -p` = **ein Prompt rein, ein Ergebnis raus**. Kein REPL, kein Hin und Her.

→ Damit wird Claude Code zum **scriptbaren Agent**. Alles, was du im Terminal automatisieren kannst, kannst du `claude -p` übergeben.

---

# Wie `claude -p` funktioniert

````md magic-move {lines: true}
```bash
claude -p "<prompt>"
```
```bash
claude -p "<prompt>" \
  --allowedTools "Bash(agent-browser*)"
```
```bash
claude -p "<prompt>" \
  --allowedTools "Bash(agent-browser*)" \
  --append-system-prompt "Du bist ein Senior QA-Engineer."
```
```bash
claude -p "<prompt>" \
  --allowedTools "Bash(agent-browser*)" \
  --append-system-prompt "Du bist ein Senior QA-Engineer." \
  --max-turns 15
```
```bash
claude -p "<prompt>" \
  --allowedTools "Bash(agent-browser*)" \
  --append-system-prompt "Du bist ein Senior QA-Engineer." \
  --max-turns 15 \
  --model opus \
  --output-format json
```
````

---

# Erstes QA-Experiment

```bash
claude -p "Open https://workout-tracker-ten-pi.vercel.app \
using agent-browser cli.

Test:
1. Lädt die Homepage? (snapshot)
2. Funktioniert die Navigation? (2 Links klicken)
3. Gibt es JS-Errors? (console)

Report: PASS/FAIL pro Test + gefundene Bugs" \
  --allowedTools "Bash(agent-browser*)"
```

Ein Befehl. Claude öffnet den Browser, klickt sich durch, schaut in die Console — und liefert einen Bericht.

---

# Das Ergebnis

| # | Test | Result |
|---|------|--------|
| 1 | **Homepage laden** | **PASS** — Onboarding-Overlay erscheint, nach "Skip" zeigt die Homepage Kalender, "Start New Workout", "Log Past Workout", "Quick Timer" und "Recent Workouts" korrekt an. |
| 2 | **Navigation (2 Links)** | **PASS** — "Workouts" navigiert zur Workouts-Seite (Templates/Benchmarks/Progressions Tabs mit 4 Templates sichtbar). "Exercises" navigiert zur Exercise-Library (173 Exercises mit Filtern nach Muskelgruppe und Equipment). |
| 3 | **JS-Errors (Console)** | **PASS** — Keine JavaScript-Fehler oder unhandled Promise-Rejections gefunden. |

**Gefundene Bugs:** Keine. Die App lädt sauber, Navigation funktioniert, keine Console-Errors.

---

# Aber Moment — testet das wirklich wie ein QA-Engineer?

"Lädt die Homepage?" und "klick 2 Links" ist kein QA-Test — das ist ein Smoke-Test. Also habe ich Claude Code selbst gefragt:

> *"Wie können wir den Prompt verbessern damit es wie ein echter QA-Engineer testet?"*

**Die Antwort:**

- 🎭 **Persona + Rubrik**: Senior QA, Given/When/Then, Severity-Skala
- 🛤️ **Echte User-Journeys** statt Klick-Tests — **Outcomes** verifizieren
- ❌ **Negative Tests**: leere Forms, ungültige Werte, doppeltes Klicken
- 🔄 **Reload-Resilienz**: überlebt der State einen Reload?
- 📋 **Strukturierter Output**: Expected vs Actual, Repro-Schritte

→ Tradeoff: längere Läufe, höhere Kosten — dafür **echte Bugs** statt "alles grün".

---

# Der verbesserte Prompt

```bash
claude -p "Teste workout-tracker als Senior QA-Engineer mit agent-browser.

JOURNEYS:
1. Workout loggen (Happy Path): Start → Exercise → Set eintragen
   → speichern → verifiziere in 'Recent Workouts'
2. Negative Test: leere Felder speichern — gibt es Validation?
3. Exercise Library: Muskelgruppe filtern → reduziert sich die Anzahl?
4. Reload-Resilienz: State nach Reload noch da?
5. Console-Errors mitloggen.

Pro Test: Given/When/Then, Expected vs Actual,
Severity (CRITICAL/MAJOR/MINOR/NONE), Repro falls Bug." \
  --append-system-prompt 'Du bist Senior QA-Engineer.
    Evidenzbasiert. Verifiziere durch Snapshots, nicht Annahmen.' \
  --allowedTools "Bash(agent-browser*)" \
  --max-turns 80
```

---

# Das neue Ergebnis: **MINOR_ISSUES** (statt "alles PASS")

| # | Finding | Severity |
|---|---------|----------|
| 1 | Set-Counter zählt leere Default-Sets — zeigt "3 Sets" statt "1" | 🟡 MINOR |
| 2 | Alle Workouts heißen default "Evening Workout" — Recent-Liste unbrauchbar | 🟡 MINOR |
| 3 | Orphan `/workout/active` State beim Initial-Load | 🟡 MINOR |
| 4 | Validation blockt leere Sets korrekt | ✅ |
| 5 | Filter reduziert 173 → 21 (Chest) korrekt | ✅ |
| 6 | State überlebt Reload (Resume Workout) | ✅ |
| 7 | Keine Console-Errors während aller Journeys | ✅ |

**Repro Finding #1:** Start Workout → 1 Exercise → nur Set 1 befüllen + complete → End Workout → Recent zeigt "3 Sets" statt "1 Set".

→ Derselbe Agent. Derselbe Browser. **Anderer Prompt — andere Bugs.**

---

# Bonus: `claude -p` ist mehr als QA

Browser-Testing ist nur **ein** Use-Case. Beispiel — ein Shopping-Agent auf otto.de:

```bash
claude -p "Öffne https://www.otto.de mit agent-browser cli.
Suche nach 'Laufschuhe Herren Größe 44'.
Filtere nach Preis unter 80€ und Bewertung 4+ Sterne.
Lege den günstigsten Treffer in den Warenkorb.
Gehe bis zur Kasse — schließe NICHT ab." \
  --allowedTools "Bash(agent-browser*)"
```

Derselbe Loop — andere Aufgabe. Auch nutzbar für Data Processing, File Organization, API Calls, Shell Aliases. Dieselben Flags gibt's im **Claude Agent SDK** (TS/Python).

💡 Wir bleiben heute beim QA-Use-Case.

---
layout: image
image: /otto-laufschuhe.png
backgroundSize: contain
---

---
layout: image
image: /a11y-audit-otto.png
backgroundSize: contain
---

---

# Was ist ein System Prompt?

Ein **System Prompt** ist die *Identität* des Modells für diesen Run — bevor irgendein User-Input kommt. Persona, Regeln, Domänenwissen, Tools.

`--append-system-prompt` hängt ihn an Claudes Default an, ohne ihn zu ersetzen.

```markdown
# QA Engineer Identity

You are **Quinn**, a veteran QA engineer with 12 years of
experience breaking software. Your job security comes from
finding bugs before users do.

## Non-Negotiable Rules
1. UI ONLY. You interact through the browser like a real user.
2. OBSERVE, DON'T ASSUME. Report what happened, not what
   you think should happen.
3. CONTINUE AFTER BUGS. One bug often reveals more.
...
```

→ Der Agent ist **kein generisches Claude** mehr — er ist Quinn, mit Meinung, Verdict-Rubrik, und Bug-Severity-Guide.

---

# Context Window

<ContextWindowSlider />

---

# Was ist ein Skill? (Progressive Disclosure)

Ein **Skill** ist ein Ordner mit `SKILL.md` — Claude lädt ihn in drei Stufen:

<SkillLoadDiagram />

- **Startup** — Nur `name` + `description` aller Skills im System-Prompt (~8k Char-Budget, 1% Context-Window). Claude weiß *dass* es den Skill gibt.
- **Invoke** — User tippt `/skill-name` oder Claude matcht die Description. Kompletter Markdown-Body wird als *eine Message* injiziert — bleibt bis Session-Ende.
- **Execute** — Script-Code landet **nie** im Kontext, nur das Output. Referenzierte `.md`-Files werden nur bei Bedarf geladen.

→ Hunderte Skills installierbar ohne Context-Explosion. Quelle: [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills)

---

# Skill: test-browser

Ein Skill, den der Implementation Agent **selbst aufrufen** kann — um zu prüfen: *"Hab ich das Feature wirklich gebaut?"*

```
1. git diff --name-only main...HEAD
2. Changed Files → betroffene Routes mappen
3. agent-browser open http://localhost:3000/<route>
4. agent-browser snapshot -i
5. Key Elements verifizieren, Console checken
6. PASS / FAIL / PARTIAL Report
```

Kein statischer E2E-Test. Der Agent liest die Diff, **entscheidet selbst**, welche Seiten relevant sind, und testet sie im echten Browser.

---
layout: image
image: /claude-review.png
backgroundSize: contain
---

---

# Und am Ende? test-browser läuft

Zwei Wege, den Verifier anzustoßen:

**🧑‍💻 Manuell — lokal:**

```bash
claude -p "Run the test-browser skill on the current branch"
```

Du triggers, der Agent testet, du siehst das Ergebnis im Terminal.

**☁️ Automatisch — in der Cloud:**

Claude Code Web, Cursor Background Agent, Copilot Coding Agent bauen das Feature in einer Sandbox. Dort ruft der Agent `test-browser` **selbst** auf — gegen einen Preview-Deploy. Du bekommst einen fertigen PR mit grünem Verifier-Report.

→ Der QA-Loop läuft **ohne dich**.

---
layout: image
image: /pr-136.png
backgroundSize: contain
---

---

# Das Endspiel

Ein **Agent**, der bei jedem Pull Request via **GitHub Actions** automatisch prüft, ob die Acceptance Criteria erfüllt sind — und darüber hinaus weitere Qualitätschecks durchführt.

<RoughSvg :width="920" :height="240" :padding="16" :roughness="1.4" :seed="13">
  <RoughRect :x="0"   :y="60" :width="220" :height="120" variant="muted"   fill-style="hachure" />
  <RoughRect :x="350" :y="60" :width="220" :height="120" variant="default" fill-style="hachure" />
  <RoughRect :x="700" :y="60" :width="220" :height="120" variant="accent"  fill-style="hachure" />

  <RoughText :x="110" :y="95"  variant="label">TRIGGER</RoughText>
  <text :x="110" :y="130" text-anchor="middle" font-size="34">🔀</text>
  <RoughText :x="110" :y="165" variant="subtitle">Pull Request</RoughText>

  <RoughText :x="460" :y="95"  variant="label">RUNTIME</RoughText>
  <text :x="460" :y="130" text-anchor="middle" font-size="34">⚙️</text>
  <RoughText :x="460" :y="165" variant="subtitle">GitHub Actions</RoughText>

  <RoughText :x="810" :y="95"  variant="label">AGENT</RoughText>
  <text :x="810" :y="130" text-anchor="middle" font-size="34">🤖</text>
  <RoughText :x="810" :y="165" variant="subtitle">Prüft ACs + Quality</RoughText>

  <RoughArrow :x1="220" :y1="120" :x2="350" :y2="120" />
  <RoughArrow :x1="570" :y1="120" :x2="700" :y2="120" />

  <RoughText :x="460" :y="225" variant="subtitle">Kein manuelles Klicken mehr — der Agent testet selbstständig.</RoughText>
</RoughSvg>

---

# Vom Laptop in die Cloud
## Zwei Claudes. Ein Vertrag. Ein QA-Loop.

---

# Der Kreislauf

<div class="mt-8 text-center text-2xl">
  Ein Claude schreibt den Testplan.<br>
  Ein anderer führt ihn aus.
</div>

<div class="mt-6 text-center text-xl opacity-70">
  Das PR-Template ist der Vertrag zwischen beiden.
</div>

<div v-click class="absolute inset-0 bg-black flex items-center justify-center">
  <QALoopDiagram />
</div>

---
layout: image
image: /pr-136.png
backgroundSize: contain
---
---

# Das Ergebnis zuerst

Bevor wir YAML lesen: so sieht das Zielbild aus.

- PR auf
- QA-Agent läuft in GitHub Actions
- Sticky Comment landet direkt am Pull Request
- Critical Bugs blocken den Merge

> Nicht "nice to have Doku", sondern ein ausführbarer QA-Report im Dev-Workflow.

---
---
layout: image
image: /qa-smoke-test-report.png
backgroundSize: contain
---

---

# GitHub Actions in 60 Sekunden

Stell dir vor, das Repo hat einen Butler:

- Ein Event passiert: PR geöffnet, synchronisiert, gelabelt
- GitHub schaut in `.github/workflows/`
- Ein Workflow startet
- Darin laufen Jobs auf einer frischen VM
- Ein Job besteht aus Steps: `run:` oder `uses:`

Für diesen Talk reicht eine Mental Map:

> Event → Workflow → Job → Step

---

# Schritt 1: `/pr` schreibt den Testplan

Der erste Claude läuft **lokal** beim Entwickler und verwandelt den Diff in einen QA-fähigen PR-Body.

```md
name: pr
description: Generate or update a structured pull request with
summary, acceptance criteria, QA scope, risk areas,
and executable test scenarios.
```

Was daran stark ist:

- erst User-Impact, dann Implementierungsdetails
- Acceptance Criteria als konkrete, testbare Outcomes
- QA Scope bewusst eng und time-boxed
- Manual Test Scenarios so geschrieben, dass QA sie direkt ausführen kann

---

> Der Prompt ist kein Template. Er ist bereits QA-Training für den Dev-Agent.

---
layout: two-cols-header
---

# Der Vertrag im PR-Body

::left::

Diese Sections sind nicht Doku.

- `## Summary`
- `## User Impact`
- `## Acceptance Criteria`
- `## QA Scope`
- `## Risk Areas`
- `## Manual Test Scenarios`
- `## CI Checks`

::right::

Was der Vertrag leistet:

- Dev und QA reden über dieselben Begriffe
- Der zweite Agent bekommt sauberen Kontext statt Diff-Rauschen
- Leere oder schwammige PRs fallen sofort auf
- Das Template wird von "Pflichtfeld" zu "ausführbarer Spezifikation"

---

# Schritt 2: CI liest den Vertrag

Der zweite Claude liest genau diese PR-Sections wieder aus.

```bash
extract_section() {
  awk -v h="## $1" '
    $0 == h {flag=1; next}
    flag && /^## / {flag=0}
    flag {print}
  ' <<<"$PR_BODY"
}

ACCEPTANCE_CRITERIA="$(extract_section 'Acceptance Criteria')"
QA_SCOPE="$(extract_section 'QA Scope')"
RISK_AREAS="$(extract_section 'Risk Areas')"
```

Danach landen diese Felder wieder im Prompt für den Browser-Agent.

> Das PR-Template ist damit wirklich executable.

---

# Die Brücke zwischen Laptop und CI

| Lokal | CI |
|---|---|
| `/pr` schreibt den Vertrag | Workflow liest denselben Vertrag |
| `claude -p` gegen lokalen Dev-Server | `claude-code-action` gegen Preview-Deploy |
| Terminal-Output lesen | Sticky Comment am PR |
| Noch mal probieren | Retry-Step |
| Ctrl+C nach ein paar Minuten | `timeout-minutes: 20` |
| Im Kopf bewerten | JSON-Schema + Merge Gate |

Die entscheidende Zeile:

> derselbe Prompt, dasselbe Modell, dieselben Tools, nur anderer Trigger

---

# Contract Enforcement

Was passiert, wenn der Entwickler den Vertrag schlampig ausfüllt?

- Acceptance Criteria leer
- QA Scope fehlt
- Manual Test Scenarios sind zu vage

Dann wird der Run nicht einfach "irgendwie grün".

```yaml
contract_valid: false
status: neutral_or_yellow
reason: "PR contract incomplete"
```

Der starke Punkt für QA:

> Nicht erst der Code wird getestet. Schon der Testplan wird geprüft.

---

# Der zweite Vertrag: JSON-Schema → Merge Gate

Vorne rein geht ein strukturierter PR-Contract.
Hinten raus kommt ein strukturierter QA-Contract.

```yaml
- name: Fail on critical bugs
  if: fromJSON(steps.qa.outputs.structured_output).verdict == 'CRITICAL_BUGS'
  run: exit 1
```

Claude bleibt nicht-deterministisch.
Das Schema macht den Output CI-tauglich.

- freier Text für Menschen
- feste Felder für die Pipeline
- klare Severity statt Bauchgefühl

---

# CI-Run Demo

<div class="mt-10 border border-[#ff6bed] rounded-xl p-8 bg-[#ff6bed]/8">
  <div class="text-3xl font-bold">Placeholder für dein CI-Run-Video</div>
  <div class="mt-4 text-xl opacity-80">PR wird erstellt → Workflow startet → Sticky Comment erscheint → Verdict setzt den Status.</div>
</div>

<div class="mt-8 text-lg opacity-75">
  Diese Slide funktioniert auch als kurzer Live-Bridge-Moment zwischen "Contract" und "Production".
</div>

---

# Was du nur in Production lernst

- `continue-on-error: true` plus Retry-Step, weil Agenten nicht deterministisch sind
- `concurrency:` mit `cancel-in-progress: true`, damit neue Pushes alte Runs abbrechen
- `timeout-minutes: 20`, damit dir kein Runaway-Agent Kosten produziert
- `use_sticky_comment: true`, damit Re-Runs nicht den PR zuspammen
- Action per SHA pinnen, nicht nur `@v1`, wegen Supply-Chain-Sicherheit

---

# In echt sind es nicht 12 Zeilen YAML

```mermaid
flowchart TD
    A[permissions: {}] --> B[timeout-minutes: 20]
    B --> C[concurrency cancel-in-progress]
    C --> D[pinned action SHA]
    D --> E[sticky comment]
```

Die Slide-Version zeigt das Prinzip.
Die Production-Version löst zusätzlich Ops-, Kosten- und Security-Probleme.

---

# Fork-PRs sind ein anderer Sicherheitsfall

Das Problem:

> Fremder Code plus deine Secrets ist keine gute Kombination.

Deshalb braucht der Workflow einen Guard:

```yaml
if: github.event.pull_request.head.repo.full_name == github.repository
```

Für Forks heißt das in der Praxis:

- kein blindes Ausführen mit Secrets
- lieber zweistufig: prüfen, dann bewusst freigeben
- Human-in-the-loop ist hier kein Bug, sondern das Sicherheitsmodell

---

# Die eine Idee zum Mitnehmen

<div class="mt-8 text-4xl leading-tight">
Ein Claude schreibt den <span class="text-[#ff6bed]">Testplan</span>.<br>
Ein anderer führt ihn aus.<br>
Das PR-Template ist der <span class="text-[#ff6bed]">Vertrag</span> zwischen beiden.
</div>

<div class="mt-10 text-xl opacity-80">
Die Rolle von QA verschiebt sich damit nach oben:
</div>

- weniger Klickarbeit
- mehr Contracts, Severity-Modelle und klare Acceptance Criteria
- mehr Systemdesign für Qualität statt nur Testausführung

---
layout: image
image: /app-screenshots-example.png
backgroundSize: contain
---

---

# Bonus: app-screenshots Skill

Ein **Skill**, den ich gebaut hab — nutzt ebenfalls Agent Browser.

Du sagst zum Agent:

> *"Screenshot the app"*

…und bekommst eine **Markdown-Doku** mit annotierten Screenshots zurück:

- 🔍 entdeckt Seiten über die Navigation
- 📸 macht Screenshots mit SVG-Annotationen direkt im DOM
- 📝 generiert Markdown mit nummerierten Referenzen

Funktioniert auf lokalen Dev-Servern **und** Live-Sites.

<div class="text-xs opacity-60 mt-2">github.com/alexanderop/app-screenshots</div>

---

# Skill zum Mitnehmen

<div class="flex flex-col items-center gap-4">
  <img src="/app-screenshots-qr.png" class="w-64 h-64 rounded-lg bg-white p-4" />
  <div class="opacity-80">github.com/alexanderop/app-screenshots</div>
</div>

---

# Und jetzt: Claude steuert deinen Computer

<div class="flex flex-col items-center gap-3">
  <img src="/claude-computer-use.png" class="rounded-lg max-h-96" />
  <div class="opacity-70 text-sm">Claude Code kann jetzt auch deinen Computer benutzen — hier editiert er live in iMovie.</div>
</div>

---

# The Bitter Lesson

<div class="text-sm opacity-60 mb-4">Rich Sutton, März 2019</div>

> "The biggest lesson that can be read from 70 years of AI research is that **general methods that leverage computation** are ultimately the most effective, and by a large margin."

<div class="mt-6 text-lg opacity-85">
Chess, Go, Speech Recognition, Vision — überall dasselbe Muster:<br>
Menschen bauen ihr Domänenwissen ein. Es hilft kurzfristig. Dann kommt Skalierung und überholt alles.
</div>

<div class="mt-6 text-xl">
Die zwei Dinge, die mit Compute skalieren: <span class="text-[#ff6bed]">Search</span> und <span class="text-[#ff6bed]">Learning</span>.
</div>

---

# Was heißt das für QA?

<div class="text-2xl leading-relaxed">
Der Reflex ist: "Ich schreibe dem Agent genau rein, <span class="opacity-60">wie</span> er testen soll."
</div>

<div class="mt-6 text-2xl leading-relaxed">
Die bittere Lektion sagt: Bau lieber den <span class="text-[#ff6bed]">Loop</span>, in dem der Agent selbst suchen und lernen kann.
</div>

<div class="mt-10 opacity-80">

- **Nicht** hart verdrahtete Click-Pfade → **sondern** ein Agent mit Browser-Tools und klarem Ziel
- **Nicht** eine perfekte Prompt-Bibel → **sondern** ein PR-Contract, an dem sich der Agent selbst misst
- **Nicht** QA-Wissen als Skript → **sondern** QA-Wissen als Acceptance Criteria, die skalieren

</div>

<div class="mt-8 text-lg opacity-70">
"We want AI agents that can discover like we can, not which contain what we have discovered."
</div>

---

# Take-Away

> **AI macht QA nicht überflüssig — sie verschiebt QA von *Tippen* zu *Denken*.**

**Für Manager:** Der Hebel ist nicht mehr "wer testet?", sondern "was heißt eigentlich *funktioniert*?".

**Für Devs:** Bau dir den Loop selbst. Lokal mit `claude -p`, in CI mit `claude-code-action`. Dieselben Flags.

**Für Montagmorgen:** Nimm **einen** Smoke-Test. Lass ihn in einem PR-Workflow laufen. Den Rest baust du iterativ.

---

layout: end
---

# Danke!

**Alexander Opalic** · Quality Night Hamburg 2026

Fragen?
