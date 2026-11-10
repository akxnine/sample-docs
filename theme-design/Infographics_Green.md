# Design & Technical Specification: AI Architecture Infographics Collection

**Document Version:** 1.0  
**Target Artifact:** `index.html` (Single-File Interactive SVG & CSS Infographic Suite)  
**Scope:** 6 Interactive AI Systems & Agent Engineering Posters  

---

## 1. Executive Summary & Overview

The **AI Architecture Infographics Collection** is a self-contained, single-file web application (`index.html`) that faithfully recreates six technical AI engineering posters using pure HTML5, Tailwind CSS, custom CSS variables, and high-precision inline SVGs.

### Core Objectives
1. **Vector Precision:** Replace static rasterized social infographics with crisp, infinitely scalable DOM and SVG diagrams.
2. **Dual Aesthetic System:** Support two distinct visual languages within a unified navigation shell:
   - **Editorial Technical Broadsheet (Posters 1–3):** Warm newsprint paper, high-contrast literary serifs, dashed grid dividers, and monospace annotations.
   - **Modern Geometric Canvas (Posters 4–6):** Crisp dot-grid backgrounds, radial ambient glows, neo-brutalist offset card shadows, and bold geometric sans-serif headings with yellow marker highlights.
3. **Interactive Pedagogy:** Enhance static diagrams with micro-interactions (tool call simulation, signal-ball path isolation, and loop iteration stepping) while preserving the exact visual fidelity of the original reference designs.
4. **Distraction-Free Technical Focus:** Strip out social media chrome (handles, "Follow for more" blocks, audio mute buttons, and carousel swipe arrows) so each poster ends cleanly on its core technical takeaway.

---

## 2. Global Visual Design System

### 2.1 Color Palette & CSS Custom Properties

The color palette centers on an **organic forest green, warm gold/yellow, and ink-black** triad over warm paper or crisp dot-grid backgrounds.

| Token / Variable | Hex Value | Role & Usage |
| :--- | :--- | :--- |
| **Canvas & Backgrounds** | | |
| `body` (Outer Viewport) | `#e4e7e2` | Soft sage-gray backdrop framing the poster sheets |
| `--bg-paper` | `#f9f8f3` | Editorial warm cream paper background (Posters 1–3) |
| `.poster-modern` base | `#fcfdfc` | Crisp white-mint dot-grid canvas (Posters 4–6) |
| **Typography & Ink** | | |
| `--ink-dark` | `#181b18` / `#141715` | Primary headings, heavy strokes, and terminal nodes |
| `--ink-body` | `#4a514c` / `#4d544f` | Editorial body paragraphs and secondary explanations |
| `--ink-muted` | `#6c746e` / `#727a73` | Monospace captions, axis labels, and subtle hints |
| **Greens (Agent / System / Success)** | | |
| `--green-deep` | `#143d27` | Deep forest accents |
| `--green-dark` | `#1d5c3f` | Primary structural green (Policy check, Lead agent, MoE bars) |
| `--green-bright` | `#0d8a47` | Modern highlight green (Posters 4–6 titles, active loop arc, offset shadows) |
| `--green-mid` | `#7bb28f` / `#78b18d` | Mid-tone bar fills (Memory files, dense FLOP comparison) |
| `--green-sage` | `#c3e2cb` | Card headers (`Real Generalization`, `Protected Competence`) |
| `--green-pale` | `#dfece2` / `#e2efe5` | Inactive bar tracks, context blocks, and passive tool buttons |
| **Yellows (Model / Active Compute / Signals)** | | |
| `--yellow-bright` | `#f4c83a` / `#f4c534` | Active tool selection, `ctx.append(r)`, signal balls, MoE top-k bars |
| `--yellow-vivid` | `#f9d423` / `#fae033` | Modern accent yellow (`MODEL` core, marker underline, badges) |
| `--yellow-header` | `#f8de6e` | Card header banners (`Precise Error Signals`, `Observability Layer`) |
| `--yellow-cream` | `#fbf4db` / `#fbf3d9` | Soft card body tint (`Protected Competence`) |
| **Semantic Accents** | | |
| Deny / Error Border | `#9e2a2b` | Blocked tool call border in Poster 1 (`deny / blocked`) |
| Border Dash | `#8e968f` | 1.5px dashed section dividers across Editorial posters |

---

### 2.2 Typography System

Loaded via Google Fonts, the suite pairs four typefaces to distinguish between editorial narrative, modern geometric diagrams, and machine/code layers:

| Font Family | CSS Class | Weights | Usage |
| :--- | :--- | :--- | :--- |
| **Fraunces** | `.font-display` | `600`, `700` | Main poster titles (`33px–53px`) and section headings (`22px`) on Posters 1–3. Uses tight tracking (`-0.022em`). |
| **Source Serif 4** | `.font-serif-body` | `400`, `600`, `700` | Subtitles (`18px–22.5px`) and explanatory body copy (`15px`) on Posters 1–3. |
| **Plus Jakarta Sans** | `.font-modern`, `.svg-modern` | `500`, `600`, `700`, `800` | Main titles (`40px–58px`), formula pills, node titles, and taglines on Posters 4–6. |
| **JetBrains Mono** | `.font-mono-tech`, `.svg-mono` | `400`, `500`, `600`, `700` | All code blocks, JSON payloads, diagram labels, metrics, state bars, and top navigation controls. |

---

### 2.3 Container & Surface Styles

1. **Editorial Sheet (`.poster-editorial` — Posters 1, 2, 3):**
   - **Max Width:** `960px`
   - **Padding:** `34px 32px 28px`
   - **Dividers:** `1.5px dashed #8e968f` (`.dashed-b`, `.dashed-t`, `.dashed-r-md`) creating a classic 2-column technical newspaper layout.
2. **Modern Geometric Sheet (`.poster-modern` — Posters 4, 5, 6):**
   - **Max Width:** `920px`
   - **Background:** Multi-layered CSS `radial-gradient` combining:
     - Soft green ambient glow at `(12%, 38%)`
     - Soft yellow ambient glow at `(88%, 75%)`
     - `18px × 18px` dot matrix (`#d5ddd7 1px`)
   - **Title Highlight (`.eng-highlight`):** Green text (`#0d8a47`) with a `::after` pseudo-element (`height: 13px`, `background: #fae043`) positioned behind the baseline.
   - **Offset Neo-Brutalist Shadows:**
     - `.shadow-offset-green`: `7px 7px 0px #0d8a47`
     - `.shadow-offset-yellow`: `7px 7px 0px #f7cf2a`
     - `.shadow-offset-green-sm` / `.shadow-offset-yellow-sm`: `5px 5px 0px` for smaller cards.

---

## 3. Navigation & Application Shell

- **Sticky Top Switcher (`<nav>`):**
  - Remains pinned at `top: 8px` (`z-50`) with a translucent blurred background (`bg-white/95 backdrop-blur`).
  - Provides 7 view modes via `switchPoster(target)`:
    - Individual poster views (`p1` through `p6`)
    - **All 6 Stacked (`all`):** Default view displaying all 6 posters sequentially with `mb-12` spacing.

---

## 4. Poster-by-Poster Architecture & Specifications

### Poster 1: "What Is an Agent Harness?"
* **Style:** Editorial 2-Column Grid (`#poster-p1`)
* **Subtitle:** *"Everything around the model that turns it into an agent. Save this for later."*
* **Grid Cells (6 Panels):**
  1. **The loop: think, act, observe (Top-Left):**
     - Left: SVG circular dashed loop (`viewBox="0 0 230 185"`) with 4 pill nodes (`model` with yellow token dot, `tool call`, `harness runs`, and yellow `result`) orbiting a central `answer` exit arrow.
     - Right: 6-line Pythonic pseudocode box (`while not done:`) with `ctx.append(r)` highlighted in `#f4c534`.
  2. **Context: what the model sees (Top-Right):**
     - Segmented horizontal progress bar representing a `200K tokens` context window at `64% used` with a vertical dashed `compact here` threshold line.
     - 6-item color legend (`system prompt`, `tool schemas`, `memory files`, `messages`, `tool results`, `summary`).
  3. **Tools: schemas in, JSON calls out (Middle-Left — Interactive):**
     - Left column: 5 clickable tool buttons (`read_file`, `edit_file`, `bash`, `web_search`, `mcp: github`).
     - Right column: Live `model output` JSON card (`type: "tool_use"`) and green `harness runs it` result banner that dynamically updates when a user clicks any tool.
  4. **Permissions and sandboxing (Middle-Right):**
     - SVG routing diagram (`viewBox="0 0 395 154"`) showing incoming tool calls passing through a green `policy check` node and branching via cubic Bézier curves into `allow (runs now)`, `ask user (approve?)`, or `deny (blocked)`.
  5. **Memory outlives the context (Bottom-Left):**
     - SVG 3-session horizontal timeline (`viewBox="0 0 405 142"`) comparing `context (resets)`, `to-do file (this task)`, and `memory file (forever)` across `session 1`, `session 2`, and `session 3`.
  6. **Subagents: split the work (Bottom-Right):**
     - SVG fan-out diagram (`viewBox="0 0 400 156"`) where a green `lead agent` box (`lead context stays small`) delegates to 3 yellow subagent boxes (`search code`, `read docs`, `run tests`), each with its `own fresh context` and returning a short summary.
* **Footer Summary Bar:**
  - Full-width 14-segment comparison bar contrasting `Model` (`1 reply`) vs. `Agent` (`until done`, alternating green model turns and yellow harness turns), paired with the core equation: *"Agent = model + harness. Model thinks, harness acts."*

---

### Poster 2: "The Self-Evolving Agent Harness"
* **Style:** Editorial Full-Canvas Flowchart (`#poster-p2`)
* **Subtitle:** *"An agent that fixes its own failures, without breaking what works. Save this."*
* **Master SVG Flowchart (`#selfEvolvingSvg`, `viewBox="0 0 920 795"`):**
  - **Central Vertical Spine:**
    - `Input` user icon $\rightarrow$ `Perception Layer` (with vertical green `Input` tab) $\rightarrow$ `Reasoning Engine / LLM` (with vertical yellow `Think` tab; Chain-of-Thought / ReAct / Plan-and-Execute) $\rightarrow$ `Can Answer Directly?` decision diamond $\rightarrow$ `Protected Competence` $\rightarrow$ `Observability Layer`.
  - **Left Diagnostic & Planning Wing:**
    - `Precise Error Signals` card: Compares failed trajectory $\tau_{\text{fail}}$ (with yellow highlight at `Step 3: First Divergence`) against reference trajectory $\tau_{\text{ref}}$, linked via a bidirectional `Reinforced Feedback` loop.
    - `Goal achieved?` diamond $\rightarrow$ `Planning Module` (with vertical green `Plan` tab; breaks goal into `Step 1 → Step 2 → Step 3`).
    - `The Self-Improvement Loop` card: Contains `Self-Update Unit` with dashed sub-boxes for `Self-Rewrite: Prompts, Tools, Logic` and `Update Checkpoints`.
  - **Right Generalization & Evolution Wing:**
    - `Real Generalization` card: Displays 3 green dashed error clusters (`Tool Usage Errors`, `Reasoning Mistakes`, `Planning / Premature Stop`) vs. 1 yellow `One-off Case`, explaining shortcut hacks vs. generalizable fixes.
    - `Protected Competence` gate pipeline: `Candidate harness update` $\rightarrow$ `Gate 1: Quality Gate` $\rightarrow$ `Gate 2: Performance Gate` $\rightarrow$ `Reject` / `Accept`.
    - `The Result: Reliable Self-Evolution` card: 4-node diamond cycle (`Precise Diagnosis`, `Generalization`, `Regression Protection`, `Validated Updates`) around `Trusted Improvement`.
* **Interactive Signal-Ball System:**
  - 4 distinct ball types travel along the edges:
    1. **Task & trace flow (`ball-task`):** Yellow fill (`#f4c83a`) with dark stroke.
    2. **Decisions & diagnosis (`ball-decision`):** Solid black fill (`#181b18`).
    3. **Re-reasoning signals (`ball-rereason`):** White fill (`#ffffff`) with dark stroke.
    4. **Results & outputs (`ball-result`):** Forest green fill (`#1d5c3f`).
  - Users can toggle the global CSS pulse animation (`toggleBallPulse()`) or click any of the 4 legend cards (`filterBalls(type)`) to dim unrelated balls (`opacity: 0.16`) and highlight the chosen signal category (`scale(1.28)` + drop-shadow glow).

---

### Poster 3: "Understanding MoE"
* **Style:** Editorial 2-Column Grid (`#poster-p3`)
* **Subtitle:** *"Mixture-of-Experts: giant models that use only a few experts per token. Save this."*
* **Grid Cells (6 Panels):**
  1. **1. Dense vs MoE (Top-Left):**
     - Compares a yellow `dense FFN` block (4×6 matrix of 24 active green weight dots where *all weights, every token* run) against an `MoE layer (8 experts, top-2)` where a black `router` pill activates only `E3` and `E8` (*2 of 8 experts run*).
  2. **2. The router picks top-k (Top-Right):**
     - Softmax bar chart across `E1`–`E8` highlighting `E4 (0.37)` and `E7 (0.28)` in yellow while the other 6 experts stay muted (`weight 0, never computed`).
     - Right column shows top-2 renormalization ($E_4: 0.57$, $E_7: 0.43$) and weighted sum $\text{output} = 0.57 \times E_4(x) + 0.43 \times E_7(x)$.
  3. **3. Where MoE lives (Middle-Left):**
     - Dashed transformer layer diagram (`× N layers`) showing `self-attention (dense)` $\rightarrow$ `add & norm` $\rightarrow$ `router` + 8-expert `MoE FFN (was a dense FFN)` $\rightarrow$ `add & norm`.
  4. **4. Total vs active parameters (Middle-Right):**
     - Log-scale horizontal bar comparison of total (light green) vs. active per-token (yellow) parameters across `Mixtral 8x7B` (`46.7B / 12.9B active`), `Qwen3-235B-A22B`, `Llama 4 Maverick`, and `DeepSeek-V3`.
  5. **5. Keep the experts balanced (Bottom-Left):**
     - Side-by-side 8-expert histograms comparing `no balancing` (severe overload on experts 1 and 2) vs. `with aux loss` (even distribution around the dashed `fair share` line), annotated with $\text{aux loss} = \alpha \times N \times \sum (f_i \times P_i)$.
  6. **6. The catch: memory (Bottom-Right):**
     - Compares `Mixtral 8x7B in 16-bit, per token`: `GPU memory needed` (`~93 GB`, black bar) vs. `compute per token` (`~26 GFLOPs`, dark green bar) vs. `a dense 46.7B model`.
* **Footer Routing Matrix:**
  - 6×8 token-to-expert routing heatmap (`The`, `cat`, `sat`, `on`, `the`, `mat` across `E1`–`E8`) illustrating how each token activates a different pair of experts.

---

### Poster 4: "Harness Engineering"
* **Style:** Modern Geometric Canvas (`#poster-p4`)
* **Header:** Eyebrow `THE SCAFFOLD · HARNESS`, title `Harness Engineering`, and pill equation `[Agent] = [Model] + [Harness]`.
* **Central Diagram (`viewBox="0 0 820 495"` inside `.shadow-offset-green` container):**
  - Top Badges: `THE HARNESS` (left) and `USER TASK ↓` (center entry pill).
  - **GUIDES (what it follows — Top Band):** `System prompt (role + rules)`, `AGENTS.md (team conventions)`, `Constraints (hard limits)` feeding dashed rules into the model.
  - **CONTEXT (what it sees — Left Column):** `Memory (past sessions)`, `Retrieval (the right docs)`, `Files & state (the working set)`.
  - **MODEL (Center Core):** Rounded yellow square (`#f9d71c`) with ambient radial glow, `reasons + decides` subtitle, and black `READING` status pill.
  - **TOOLS (what it touches — Right Column):** `Tool registry (what it can call)`, `Sandbox (safe execution)`, `Permissions (ask before risky)`.
  - **SENSORS (how it gets checked — Bottom Band):** `Tests & evals (did it work?)`, `Output checks (schema + lint)`, `Traces (log every step)`, plus a dashed yellow `↺ retry w/ feedback` loop back into `MODEL` and a stepped exit line to the `✓ VERIFIED OUTPUT` bottom pill.
* **Footer Tagline:** *"Same model. Better harness. Better agent."*

---

### Poster 5: "Loop Engineering"
* **Style:** Modern Geometric Canvas (`#poster-p5`)
* **Header:** Eyebrow `THE CYCLE · LOOP`, title `Loop Engineering`, and dark code pill `while (!goal_met) { observe → reason → act → check }`.
* **Interactive 5-Stage Circular Loop Diagram (`#loopEngSvg`, `viewBox="0 0 820 455"`):**
  - **Central Status Circle:** Displays `ITERATION 03 /10`, `goal: tests passing 8/12`, a dynamic green progress bar, and 3 status dots.
  - **Outer Ring & 5 Clickable Stage Cards (`setLoopStep(1..5)`):**
    1. `01 OBSERVE (state + errors)` — 12 o'clock
    2. `02 REASON (plan the next move)` — 2 o'clock (highlighted with active green arc and yellow bullseye token marker)
    3. `03 ACT (edit · run · tools)` — 4:30
    4. `04 CHECK (tests · evals)` — 7:30
    5. `05 DECIDE (met? stop : loop)` — 10 o'clock, featuring a `LOOP ↺` badge and a dashed green exit path (`exit when goal met`) to the `DONE ✓` pill.
* **Bottom Dual Cards:**
  - **STOP CONDITIONS (`.shadow-offset-yellow-sm`):** `✓ Goal: all tests green`, `↺ Max 10 laps / 30 min`, `$ Hard token budget`.
  - **MEMORY BETWEEN LAPS (`.shadow-offset-green-sm`):** `✎ progress.md what's done`, `⑂ A git commit per lap`, `○ Fresh context each lap`.
* **Footer Tagline:** *"The prompt starts it. The loop finishes it."*

---

### Poster 6: "Graph Engineering"
* **Style:** Modern Geometric Canvas (`#poster-p6`)
* **Header:** Eyebrow `THE MAP · GRAPH`, title `Graph Engineering`, subtitle *"Nodes do the work. Edges decide what runs next. Shared state carries everything between them."*, and a 6-pill node legend (`LLM`, `Tool`, `Human`, `Router`, `Eval`, `Checkpoint`).
* **Support Agent State-Graph Flowchart (`viewBox="0 0 820 450"` inside `.shadow-offset-yellow` container):**
  - **Entry & Intent Classification:** `START` pill $\rightarrow$ `Classify ticket (llm · sets intent)` $\rightarrow$ Checkpoint #1 $\rightarrow$ Black Diamond Router (`route(state.intent) →`).
  - **Left Branch (`refund`):** `Check policy (tool · eligible?)` $\rightarrow$ Checkpoint #2 $\rightarrow$ `|| Human approval (interrupt · waits)` (dashed green border) $\rightarrow$ `Issue refund (tool · payments)` $\rightarrow$ `END`.
  - **Center Callout Card:** Dashed note box `INCOMING TICKET · RUN 2: “How do I export my data to CSV?”`.
  - **Right Branch (`question` + `parallel ↓`):** Splits into `Search docs (tool · retrieval)` and `Past tickets (tool · history)`, merges into highlighted yellow `Draft reply (llm · merges both)` (with green halo and active token square) $\rightarrow$ Checkpoint #3 $\rightarrow$ solid black `Quality check (eval · score ≥ 0.85)` with a dashed yellow `retry` loop back to `Draft reply`, or forward to `END`.
* **Dark Shared State Bar (`SHARED STATE` — `checkpoint #3 · saved`):**
  - 4-column dark terminal grid (`#111412`) inspecting live graph state keys:
    - `intent`: `"question"`
    - `context`: `docs: 2 · tickets: 3`
    - `review`: `v1 · score 0.62 ✕` (highlighted border indicating why the retry edge triggered)
    - `result`: `—`
* **Footer Tagline:** *"Prompts suggest. Edges enforce."*

---

## 5. Interactive State & JavaScript Architecture

All interactivity is written in vanilla ES6 JavaScript embedded at the bottom of `index.html` with zero external framework dependencies:

| Function / Handler | Target Poster | Behavior |
| :--- | :--- | :--- |
| `switchPoster(target)` | Global Nav (`p1`–`p6`, `all`) | Toggles `.hidden` on `<article id="poster-pX">` elements, updates active button styling in the sticky header, and smoothly scrolls to the top of the viewport. |
| `.tool-btn` click listener | Poster 1 (`#toolList`) | Updates `#jsonToolName`, `#jsonToolInput`, and `#jsonToolResult` from the `toolPayloads` dictionary and moves the yellow `#f4c534` active highlight to the clicked tool button. |
| `filterBalls(type)` | Poster 2 (`#selfEvolvingSvg`) | Isolates `.ball-{type}` elements (`task`, `decision`, `rereason`, `result`) by applying `.ball-active-glow` to matches and `.ball-dimmed` to non-matches. Clicking the active category again resets the filter. |
| `toggleBallPulse()` | Poster 2 (`#poster-p2`) | Toggles `.balls-animating` on the Poster 2 container, pausing or resuming the staggered keyframe animation (`pulseFlow`). |
| `setLoopStep(step)` | Poster 5 (`#loopEngSvg`) | Updates `#loopIterNum`, `#loopGoalText`, `#loopProgressBar` width, and `#loopHeadMarker` SVG coordinates (`translate(x, y)`) when any of the `01`–`05` loop stage cards are clicked. |

---

## 6. Responsive & Print Considerations

- **Horizontal SVG Scroll Containers:** Complex wide flowcharts (Posters 2, 4, 5, and 6) are wrapped in `overflow-x-auto` containers with `min-w-[720px]` to `min-w-[780px]` inner bounds so node typography and connector arrows never crush or overlap on narrow mobile screens.
- **Responsive Grid Breakpoints:** Posters 1 and 3 use `grid-cols-1 md:grid-cols-2` so the 6-cell dashed grid stacks cleanly into a single column on viewports below `768px`, automatically hiding vertical right-hand dashed borders on mobile and restoring them via `.dashed-r-md` on desktop.