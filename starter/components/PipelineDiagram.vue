<script setup lang="ts">
import { ref, computed, shallowRef, watchEffect } from 'vue'

type StepId = 'pr' | 'extract' | 'template' | 'claude' | 'stream' | 'archive'

interface Step {
  id: StepId
  title: string
  subtitle: string
  detail: string
}

const steps: Step[] = [
  {
    id: 'pr',
    title: 'PR Context',
    subtitle: 'fixture | gh pr view',
    detail: `# Fixture (reproducible) oder Live-PR
if [[ -n "$PR_FIXTURE" ]]; then
  PR_TITLE="$(head -n1 "$PR_FIXTURE" | sed 's/^TITLE: //')"
  PR_BODY="$(tail -n +2 "$PR_FIXTURE")"
elif [[ -n "$PR_NUMBER" ]]; then
  PR_JSON="$(gh pr view "$PR_NUMBER" --json title,body)"
  PR_TITLE="$(jq -r .title <<<"$PR_JSON")"
  PR_BODY="$(jq -r .body  <<<"$PR_JSON")"
fi`,
  },
  {
    id: 'extract',
    title: 'Extract sections',
    subtitle: 'Summary · AC · Risk · QA-Scope',
    detail: `# Zieht ## Summary / ## Acceptance Criteria / ...
# aus dem PR-Body – selbe Felder wie der CI-Workflow
extract_section() {
  awk -v h="## $1" '
    $0 == h {flag=1; next}
    flag && /^## / {flag=0}
    flag {print}
  ' <<<"$PR_BODY"
}
PR_SUMMARY="$(extract_section Summary)"
ACCEPTANCE_CRITERIA="$(extract_section 'Acceptance Criteria')"
RISK_AREAS="$(extract_section 'Risk Areas')"`,
  },
  {
    id: 'template',
    title: 'Prompt template',
    subtitle: '{{PLACEHOLDERS}} → Python substitute',
    detail: `# Multi-line-sicher via Python statt sed
PROMPT="$(python3 -c '
import os, sys
txt = open(os.environ["PROMPT_FILE"]).read()
for k in ["PR_TITLE","PR_BODY","ACCEPTANCE_CRITERIA",
          "RISK_AREAS","QA_SCOPE","APP_URL","DATE"]:
    txt = txt.replace("{{"+k+"}}", os.environ.get(k, ""))
sys.stdout.write(txt)
')"`,
  },
  {
    id: 'claude',
    title: 'claude -p',
    subtitle: '--append-system-prompt · stream-json',
    detail: `claude -p "$PROMPT" \\
  --model claude-opus-4-6 \\
  --max-turns 100 \\
  --allowedTools "Bash(agent-browser *),Write,Read,Grep" \\
  --append-system-prompt "$SYSTEM_PROMPT" \\
  --output-format stream-json \\
  --verbose`,
  },
  {
    id: 'stream',
    title: 'Live render',
    subtitle: 'tee + jq → Terminal',
    detail: `# Ein JSON-Event pro Turn → live lesbarer Log
| tee qa-stream.ndjson \\
| jq -r --unbuffered '
    if .type == "assistant" then
      (.message.content[]
       | if .type == "tool_use"
         then "→ \\(.name) " + (.input.command // "")
         else "… " + (.text // "") end)
    elif .type == "result" then
      "◆ done · \\(.num_turns) turns · $\\(.total_cost_usd)"
    else empty end'`,
  },
  {
    id: 'archive',
    title: 'Archive run',
    subtitle: 'qa-archive/<ts>-<focus>/',
    detail: `ARCHIVE_DIR="qa-archive/$(date +%Y%m%d-%H%M%S)-$FOCUS"
mkdir -p "$ARCHIVE_DIR"
for f in qa-stream.ndjson qa-structured-output.json qa-report.md; do
  [[ -f "$f" ]] && cp "$f" "$ARCHIVE_DIR/"
done

# → Prompts iterieren, Runs vergleichen, nichts geht verloren.`,
  },
]

const selected = ref<StepId>('pr')
const current = computed(() => steps.find(s => s.id === selected.value)!)

const highlighted = shallowRef<string>('')

function escapeHtml(value: string): string {
  return value
    .replaceAll('&', '&amp;')
    .replaceAll('<', '&lt;')
    .replaceAll('>', '&gt;')
    .replaceAll('"', '&quot;')
    .replaceAll("'", '&#39;')
}

watchEffect(async () => {
  const code = current.value.detail
  highlighted.value = `<pre class="code-block"><code>${escapeHtml(code)}</code></pre>`
})
</script>

<template>
  <div class="pipeline-diagram">
    <div class="nodes">
      <button
        v-for="(step, i) in steps"
        :key="step.id"
        class="node"
        :class="{ active: selected === step.id }"
        @click="selected = step.id"
      >
        <div class="node-index">{{ i + 1 }}</div>
        <div class="node-body">
          <div class="node-title">{{ step.title }}</div>
          <div class="node-subtitle">{{ step.subtitle }}</div>
        </div>
      </button>
    </div>

    <div class="detail">
      <div class="detail-header">
        <span class="detail-dot" />
        {{ current.title }}
      </div>
      <div class="detail-code" v-html="highlighted" />
    </div>
  </div>
</template>

<style scoped>
.pipeline-diagram {
  display: grid;
  grid-template-columns: 320px 1fr;
  gap: 24px;
  font-family: var(--slidev-font-sans, system-ui);
}

.nodes {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.node {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 14px;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  color: inherit;
  text-align: left;
  cursor: pointer;
  transition: all 0.15s ease;
  position: relative;
}

.node::after {
  content: '';
  position: absolute;
  left: 22px;
  top: 100%;
  width: 2px;
  height: 8px;
  background: rgba(255, 255, 255, 0.15);
}

.node:last-child::after {
  display: none;
}

.node:hover {
  background: rgba(255, 107, 237, 0.08);
  border-color: rgba(255, 107, 237, 0.4);
}

.node.active {
  background: rgba(255, 107, 237, 0.12);
  border-color: #ff6bed;
  box-shadow: 0 0 0 1px #ff6bed;
}

.node-index {
  width: 22px;
  height: 22px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 11px;
  font-weight: 600;
  flex-shrink: 0;
}

.node.active .node-index {
  background: #ff6bed;
  color: #111;
}

.node-body {
  min-width: 0;
}

.node-title {
  font-size: 14px;
  font-weight: 600;
  line-height: 1.2;
}

.node-subtitle {
  font-size: 11px;
  opacity: 0.6;
  font-family: var(--slidev-font-mono, monospace);
  margin-top: 2px;
}

.detail {
  background: rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  min-height: 340px;
}

.detail-header {
  padding: 10px 16px;
  background: rgba(255, 255, 255, 0.04);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  font-size: 13px;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 8px;
}

.detail-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #ff6bed;
}

.detail-code {
  flex: 1;
  overflow: auto;
  font-size: 12px;
  line-height: 1.55;
}

.detail-code :deep(pre.code-block) {
  margin: 0;
  padding: 16px;
  background: transparent;
  font-family: var(--slidev-font-mono, 'Geist Mono', monospace);
  color: #e6edf3;
  white-space: pre;
}

.detail-code :deep(code) {
  font-family: inherit;
}
</style>
