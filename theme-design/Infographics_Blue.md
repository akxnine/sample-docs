<!-- ... existing code ... -->
## 2. Global Visual Design System

### 2.1 Color Palette & CSS Custom Properties

The color palette centers on an **engineered cobalt blue, warm gold/yellow, and deep navy-ink** triad over warm paper or crisp cool-slate dot-grid backgrounds.

| Token / Variable | Hex Value | Role & Usage | 
| ----- | ----- | ----- | 
| **Canvas & Backgrounds** |  |  | 
| `body` (Outer Viewport) | `#e1e7ef` | Soft slate-blue backdrop framing the poster sheets | 
| `--bg-paper` | `#f9f8f3` | Editorial warm cream paper background (Posters 1–3) | 
| `.poster-modern` base | `#fbfcfe` | Crisp ice-white dot-grid canvas (Posters 4–6) | 
| **Typography & Ink** |  |  | 
| `--ink-dark` | `#141923` / `#111622` | Primary navy-charcoal headings, heavy strokes, and terminal nodes | 
| `--ink-body` | `#3e4c5e` / `#425061` | Editorial slate body paragraphs and secondary explanations | 
| `--ink-muted` | `#627084` / `#68778c` | Monospace captions, axis labels, and subtle hints | 
| **Blues (Agent / System / Verification)** |  |  | 
| `--blue-deep` | `#0f2c59` | Deep navy accents and verified badge text | 
| `--blue-dark` | `#1d4e89` | Primary structural cobalt blue (Policy check, Lead agent, MoE bars) | 
| `--blue-bright` | `#0b65c6` | Modern highlight blue (Posters 4–6 titles, active loop arc, offset shadows) | 
| `--blue-mid` | `#6ea1d4` / `#7cb0e3` | Mid-tone bar fills (Memory files, dense FLOP comparison) | 
| `--blue-sage` | `#bfd9f2` / `#c7e0f8` | Card headers (`Real Generalization`, `Protected Competence`, `VERIFIED OUTPUT`) | 
| `--blue-pale` | `#e3eef9` / `#e6eff8` | Inactive bar tracks, context blocks, and passive tool buttons | 
| **Yellows (Model / Active Compute / Signals)** |  |  | 
| `--yellow-bright` | `#f4c83a` / `#f4c534` | Active tool selection, `ctx.append(r)`, signal balls, MoE top-k bars | 
| `--yellow-vivid` | `#f9d423` / `#fae033` | Modern accent yellow (`MODEL` core, marker underline, badges) | 
| `--yellow-header` | `#f8de6e` | Card header banners (`Precise Error Signals`, `Observability Layer`) | 
| `--yellow-cream` | `#fbf4db` / `#fbf3d9` | Soft card body tint (`Protected Competence`) | 
| **Semantic Accents** |  |  | 
| Deny / Error Border | `#9e2a2b` | Blocked tool call border in Poster 1 (`deny / blocked`) | 
| Border Dash | `#8996a6` | 1.5px cool-slate dashed section dividers across Editorial posters | 

### 2.2 Typography System
<!-- ... existing code ... -->
2. **Modern Geometric Sheet (`.poster-modern` — Posters 4, 5, 6):**

   * **Max Width:** `920px`

   * **Background:** Multi-layered CSS `radial-gradient` combining:

     * Soft sky-blue ambient glow at `(12%, 38%)` (`rgba(196, 224, 252, 0.42)`)

     * Soft yellow ambient glow at `(88%, 75%)` (`rgba(254, 243, 185, 0.38)`)

     * `18px × 18px` cool-slate dot matrix (`#cfd9e6 1px`)

   * **Title Highlight (`.eng-highlight`):** Cobalt blue text (`#0b65c6`) with a `::after` pseudo-element (`height: 13px`, `background: #fae043`) positioned behind the baseline.

   * **Offset Neo-Brutalist Shadows:**

     * `.shadow-offset-blue`: `7px 7px 0px #0b65c6`

     * `.shadow-offset-yellow`: `7px 7px 0px #f7cf2a`

     * `.shadow-offset-blue-sm` / `.shadow-offset-yellow-sm`: `5px 5px 0px` for smaller cards.

## 3. Navigation & Application Shell
<!-- ... existing code ... -->