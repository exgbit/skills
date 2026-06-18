---
name: premium-design-loop
description: Use when improving a webpage's visual quality, craft, or "premium feel" — making a site look more expensive, high-end, and designed rather than generic or AI-made. Triggers include "make it look premium", "质感", "看起来更高级/更贵", scoring a site against premium design standards, iteratively polishing visual design, fixing the generic Inter-font AI look, doing a dedicated mobile pass, or adding tasteful micro-interactions. Works from a local code path and/or a reachable URL.
---

# Premium Design Loop

Iteratively evaluate and upgrade a webpage's craft. Each round: **checkpoint → score → optimize the weak dimensions → re-score**, until scores hit target or the iteration cap.

Core principle: **premium = restraint + finishing, not more elements.** "More expensive, not busier."

But read **Restraint ≠ suppression** below — restraint governs *elements/density*, not the light/motion richness the user asked for.

## When to Use

- A page (local path or URL) needs to look more high-end / premium / "expensive".
- A page reads as generic or obviously AI-generated (default Inter font, flat static sections, no finishing).
- You need an honest, scored design critique against a consistent rubric — then the fixes applied.
- A site "works on mobile" only by scaling down and needs a real mobile design pass.

**Not for:** building a page from scratch (use brainstorming/frontend-design first), pure copywriting, or backend work.

## The 12 Dimensions

Score each 1–10; "passing" = ≥ target (default **9**). All-12-at-9 is a high bar — most runs end `MAX_REACHED` with strong scores, which is a good outcome, not a failure.

| # | Dimension | What 9+ looks like |
|---|-----------|--------------------|
| 1 | Point of view | A clear opinion/aesthetic, not a template. Memorable, intentional. |
| 2 | Typography | Deliberate type scale, pairing, tracking, line-height. No default Inter look. |
| 3 | Colour | Restrained, intentional palette with real contrast hierarchy. No muddy defaults. |
| 4 | Hierarchy | Eye lands where it should. Clear primary/secondary/tertiary. Generous, rhythmic spacing. |
| 5 | Imagery | High-quality, consistent treatment (grade, crop, ratio). No stocky filler. |
| 6 | Motion | Subtle, refined, purposeful. Eased, not bouncy. Enhances, never distracts. |
| 7 | Mobile | Designed for small screens (hide/tighten/resize), not just scaled down. |
| 8 | Invisible finishing | Optical alignment, hover/focus states, empty states, radii/shadow consistency, micro-copy. |
| 9 | Accessibility | WCAG-level contrast, visible focus, keyboard nav, semantic markup, ARIA. |
| 10 | Performance | Fast first paint, optimized images, no jank, subset/preloaded fonts, no layout shift. |
| 11 | Design-system consistency | Spacing/size/radius/shadow come from tokens, not ad-hoc values. |
| 12 | Copy / microcopy | Has a voice and point of view. No generic AI filler ("Welcome to our website"). |

**The number is a loop-driver, not a metric.** Scores are subjective and inflate via anchoring (you feed prior scores in). Treat them as a rough "what to fix next / are we done" signal. The real deliverables are the **verdict text**, the **before/after visuals (+ GIF for motion)**, and the **user's eye**. Don't burn a re-score subagent on a tiny safe delta — state what changed and let the visual judge.

## The Craft Laws

The optimizer MUST honor these every round.

1. **Restraint over addition.** Default to removing/refining, not adding. Generic section → make it more refined, not more crowded.
2. **Tame the first motion pass.** AI's first motion attempt is always too much. After adding motion, deliberately dial back: *"more subtle, more refined"* — slower easing, smaller travel, lower opacity deltas, lagged cursor-follow not instant snapping.
3. **Kill the generic AI font.** Default `Inter`/system sans = instant "AI-made" tell. Swap for something with character (a self-hosted woff2, or a deliberate serif-display + sans/mono-body pairing).
4. **Activate static sections.** Flat sections get *restrained* micro-movement — parallax, hover reveals, subtle entrances. Tasteful, never carnival.
5. **Mobile is a design, not a resize.** Decide what to hide / tighten / reflow on small screens — don't just shrink.
6. **Tokenize the invisibles.** Spacing, radii, shadows, type sizes from one small scale. Fix optical alignment and hover/focus/empty states.

Prefer *intent* prompts ("this feels static and generic — make it more expensive with restrained cursor interaction") over micro-instructions, then tame with "more subtle, more refined."

**Premium baseline** (concrete positive defaults — what "good" looks like when none exists, all from tokens):
- **Type**: 4–5 sizes on a 1.2–1.33 ratio with a *big* jump to the display size — don't crowd 8 fuzzy sizes into a 10–18px band. Weight, not size, carries emphasis in dense UI. Serif display + clean sans/mono body is a cheap strong pairing.
- **Spacing**: 4/8px base, generous; let the hero breathe.
- **Colour**: one accent + a 4–5 step neutral ink ramp + semantic state colours, nothing else.
- **Shadow**: soft, layered (`0 1px 2px` + `0 8px 24px` at 5–10%), never one harsh drop.
- **Radius**: a small fixed set (e.g. 6/10/14px).

## Light & Motion (光影) — premium vs cheap

The strongest premium lever **and** the easiest way to look cheap. It's not "motion > static" — it's **restrained motion > static > bad motion**.

| Premium motion | Cheap motion |
|---|---|
| Slow (300–800ms+), ease-out | Fast, bouncy, spin |
| Triggered by the user (cursor / scroll / hover) | Auto-loops that never stop |
| Subtle (small travel, low-opacity light) | Big travel, high contrast, attention-grabbing |
| Quiet while the user reads | Moving in the corner of the eye while reading |

**Restraint ≠ suppression.** Craft Law 1 governs *elements/density* — not the light/motion richness the user picked in Step 1. If they chose a rich 光影 level or keep asking for "more / faster / add another," **deliver it** (kept slow + eased + reduced-motion-gated). Don't quietly shrink it back to "tasteful" against their wish.

**Toolkit that reads premium** (honor the chosen 光影 level):
- **Ambient light**: a few large, heavily-blurred glow orbs drifting on *independent, unsynced* slow loops (10–34s); low opacity; all in the brand's own hue.
- **Film grain**: a tiled SVG `feTurbulence` overlay at ~0.08–0.16 opacity to kill the flat "digital" look. Static, not flickering.
- **Depth**: lagged cursor parallax (ease toward the pointer over ~0.4–0.6s, never snap); soft gradients; occasional glass (`backdrop-filter: blur`).
- **Wordmark/hero shine**: put the highlight *in the text's own gradient fill* (animate `background-position` on a `background-clip:text` gradient) — NOT a duplicated overlay span (doubles/misaligns), NOT a light bar sweeping the page background (reads cheap/"土").

**Reads cheap — avoid/remove:** background "sweep" bands; per-character typewriters and fast frame-swaps that loop forever (slow them, play once, or cross-fade).

**Two hard rules:**
1. **Gate every JS-driven animation on `prefers-reduced-motion` in JS** (`matchMedia('(prefers-reduced-motion: reduce)')`) — a CSS media query alone does NOT stop `setInterval`/`setTimeout` motion.
2. **Motion is tuned in a live knob-loop, NOT the screenshot-score loop.** A still can't show it, so light/motion does *not* iterate through 3.2/3.5. Instead: ship a first pass → user views it live (serve + `open` the URL) or you record a GIF → **hand back stating the current knob values** ("orbs 10/13/17s · grain 0.16 · grid drift 8s · parallax on") so they steer by number → apply "faster / fewer / drop that one" → repeat. Expect many small rounds. Knobs per effect: **on/off · intensity · speed · count · travel**. Don't score motion to a 9; tune until the eye says yes.

## Execution Flow

```
START → Configure → Probe environment
      → LOOP[ checkpoint → shot(before) → score → all pass? EXIT
              : optimize weak dims → shot(after) + re-score → all pass? EXIT : cap reached? EXIT : continue ]
      → Final report
```

The cap is checked **after** a full optimize+re-score (in 3.6), never before — else a low cap exits before any optimization runs.

---

### Step 1 — Configure

`AskUserQuestion` allows **max 4 questions/call** and there are more config items than that. Lead with what changes the outcome most — **platform scope, reference anchor, light/motion intensity** (+ run-mode if unclear). State the documented defaults for the rest rather than burning questions. If the caller already specified values, use them; only ask what's missing.

- **Target**: local path and/or reachable URL. A path is required to apply fixes; a URL/local-serve to *see* rendering. URL-only → you can score but not fix (offer a one-pass score-only review, or ask for the path).
- **Run mode**: `Auto` (run all rounds, report at end) or `Step` (pause each round to confirm). Default `Step` for large in-use tools. **In `Auto`, never block mid-loop for a human decision — defer every interactive call to the final report:** motion gets one conservative first-pass (documented knob defaults, flagged *needs-live-tuning*); structural changes to an in-use tool are *not* applied but collected into a **needs-confirmation list**; a dirty working tree is handled by file-copy backup, not a stop. Auto runs the non-interactive work and reports the rest — it must not silently drop to Step or fake-wait for the user.
- **Max iterations**: default **5**. **Target score**: default **9**.
- **Swap generic fonts?**: default **yes**. **Extra dimensions** (a11y/perf/design-system/copy): default **all on**.
- **Platform scope**: `PC only` / `Mobile only` / `PC + mobile` (default **both**) — controls which viewports get shot/scored/optimized. Don't waste a viewport they didn't ask for.
- **Reference anchor(s)**: the brand/site whose premium feel to aim at (Apple, Linear, Stripe, Vercel, 無印良品, or a URL). **Ask, don't default** — it's what makes scoring real (reframes "abstract 9/10" → "as premium as `<ref>`?"). Borrow the reference's *craft*, never its layout or **identity** — keep the user's brand/mascot/palette unless they say otherwise.
- **光影 level**: `None` / `Subtle` / `Medium` / `Rich` (default **Subtle–Medium**).
- **Animation kinds** (multi-select): entrance · cursor parallax · hover micro-interactions · scroll reveal · ambient drift. Default **entrance + hover + subtle ambient**. (All slow/eased/reduced-motion-gated — see Light & Motion.)

### Step 2 — Probe environment

- **Rendering** (strongly preferred — makes colour/motion/mobile/finishing scores reliable). Probe for `claude-in-chrome` tools or a `chrome-devtools` MCP (`mcp__chrome-devtools__*`). If present → open target, screenshot desktop + a real mobile viewport.
  - **If no browser control, do NOT silently fall back to source-only** — interrupt with one `AskUserQuestion`. On confirm, enable one in a step:
    - **Claude in Chrome** (uses the user's real logged-in browser — best for gated/auth pages): install the extension (Chrome/Edge only) → `/chrome` in session. ⚠️ The Web Store extension must be added by the *user*; you can't install it. Walk them through, then re-probe.
    - **chrome-devtools MCP** (fresh browser, you install it): `claude mcp add chrome-devtools npx chrome-devtools-mcp@latest` (Node 22+, local Chrome). No saved logins.
    - **Skip → source-only (degraded)**: mark colour/motion/mobile/finishing `(inferred)`; offer to lower target to ~8 since a true 9 is unlikely without rendering.
  - Proceed source-only only if the user picks Skip (or, in `Auto`, doesn't answer — note it).
- **Locate the target, then serve it** (local path): a repo (e.g. `./web`) is usually **multi-route** — identify and confirm the specific route + source file to polish; don't assume `page.tsx` is the page they mean. Then serve: detect the framework → run its dev command (`npm run dev` etc.) → wait for the port → render the target route's URL.
- **Backup**: git repo? → checkpoints are commits. Else → copy touched files into `.design-backups/iter-N/`.

State which modes are active before the loop.

### Step 3 — The Loop

Maintain across iterations: `iteration`, `scores_history`, `changes_log`, `target_score`, `max_iterations`.

**3.1 Checkpoint (before any edit).** **Default to the file-copy backup** — copy the target page's files + shared CSS/tokens into `.design-backups/iter-N/` (widen if a later edit touches more). It sidesteps two real traps: you don't yet know which files this round edits (that's decided in 3.4), and the working tree is often already dirty with the user's unrelated changes. Use a **git-commit** checkpoint *only* if the tree is clean and the user prefers it (`git add <target files>` — never `git add -A`; no `--no-verify`). **In `Auto`, never stop to ask about a dirty tree** — the file-copy backup makes it safe. Add `.design-shots/` + `.design-backups/` to `.gitignore`. Never skip — it's the only safe rollback.

**3.2 Capture "before" shots + Score.** Screenshot the in-scope viewport(s) to `.design-shots/iter-N/before-{desktop,mobile}.png`. For mobile, emulate a phone (`390×844`, mobile flag) and **reload** before shooting — a window-resize often won't reflow. Re-capture each round so the folder is self-contained (iter 2+: "before" = prior "after").

Dispatch a `Task` (`general-purpose`) as an honest, critical reviewer. Give it:
- the `before-*` screenshots and/or source files, the 12-dim rubric, and the Craft Laws;
- **the reference anchor(s)** — and **make it visual**: screenshot the reference at the same viewport and pass *that image* alongside the target so it compares two real pictures (not "Apple from memory"). Ask it to name 3 specific things the reference does that the target doesn't;
- **the platform scope** — judge only the in-scope viewport(s);
- **weight the first screen most** — premium is decided above the fold in the first 2–3s.

**Measured, not eyeballed** where possible — but never let an *unmeasurable* dimension block a 9. **Accessibility**: compute WCAG contrast by hand from the CSS colours — relative luminance of fg & bg, ratio = (L_lighter + 0.05) / (L_darker + 0.05), need ≥4.5:1 body / ≥3:1 large-or-bold. This is always doable; run axe only if it's actually present. **Performance**: mark `(inferred)` and treat as a checklist (image weight, font strategy, CLS, no monolith re-render) unless a real Lighthouse/trace channel exists — don't pretend a score. **Motion**: judge live, don't score (see Light & Motion). Subjective dims are anchored to the reference, not an abstract ideal. Require JSON: `{scores:[{dimension, score, verdict, fixes}], overall, summary}`. Honest and specific (cite the section/selector); vague praise is failure.

**Also run a naive first-impression check.** A *fresh* subagent given ONLY the screenshot (no rubric/context): *"You're a normal visitor — does this look premium or cheap? What's the FIRST thing that feels off?"* This is closest to the real goal and catches what the rubric misses (a friend's "缺少科技感", "buttons too big"). Weight it at least as highly as the scores.

These are the round's **opening scores** (pick what to optimize). Iter 2+ reuse the prior round's closing scores instead of re-scoring the unchanged page — unless it changed outside the loop.

**3.3 Pass check.** Every dim ≥ target → exit `SUCCESS`. Else optimize. **Don't check the cap here** (it's in 3.6).

**3.4 Optimize (apply edits).** Worst dimension first. Apply the reviewer's `fixes` under the Craft Laws (swap fonts; tame motion; dedicated mobile pass; add restrained interaction to static/flat sections).
- **Surgical = no *unrelated* changes — not "small" changes.** Every edit traces to a low-scoring dimension; when many fail, a large rewrite is correct — just don't touch code unrelated to any dimension.
- **Exception — large in-use functional tools** (1000+ line component, a working app, a dense dashboard): "rewrite freely" will break things. **Safe-layer-first**, default `Step` mode: (1) first apply only changes touching **no business logic** — a11y/contrast, hover/focus, tokenized radii/shadow/spacing, framing/alignment; (2) **confirm before any structural change** (re-layout, dedupe, merge nav) — usually a *product* decision, not craft; (3) **never edit logic/state/data flow**; use grep + scoped find-replace, checkpoint every round; (4) reweight the rubric — density, scan path, cell/row alignment matter more than imagery/copy.
- **Verify it still renders before scoring.** Reload after editing (esp. TSX/JS) — a bad edit can blank the page or throw. A broken render is an auto-fail, not a low score; check the console. **A passing dev render ≠ a passing production build** — a type error can blank prod while dev only shows an overlay; run a typecheck/build before declaring done or deploying.
- Record each change in `changes_log`.

**3.5 Capture "after" shots + re-score.** Re-shoot to `.design-shots/iter-N/after-{desktop,mobile}.png`. Re-run the 3.2 reviewer on the after-state, passing this round's opening scores + `changes_log` so it judges whether each weak dim improved. These **closing scores** are the round's result → append to `scores_history`, carry forward as next round's opening.

**3.6 Pass + cap + mode gate.** Closing scores all ≥ target → `SUCCESS`. Else `iteration >= max` → `MAX_REACHED`. **Diminishing-returns brake (both modes):** if a round improved no dimension by ≥1, or every remaining gap needs assets / product decisions / a live motion-tuning pass (not more craft edits), stop early and report — don't grind to the cap for zero marginal gain. Else `Auto` → loop to 3.1. Else `Step` → show opening→closing delta + edits, confirm before next round; if user stops → `PAUSED`.

### Step 4 — Final report

**Always end by surfacing the visual progression, not just listing files:** give the concrete before/after **paths**, explain the chain, and **show the headline comparison (original vs final) inline** so the user SEES what changed. The visuals are the real deliverable — don't bury them behind a glob pattern.

```markdown
## Premium Design Loop — Complete
Exit reason: SUCCESS / MAX_REACHED / PAUSED
Rendering: chrome screenshots / source-only (inferred)
Backup: git commits / .design-backups/

### Before / after — the visual progression (show it, don't just link it)
- Original:  .design-shots/iter-1/before-{desktop,mobile}.png
- Per round: .design-shots/iter-N/after-{desktop,mobile}.png
  (iter-N's "before" = iter-(N-1)'s "after" — so original → after-1 → after-2 → … → after-final is the full chain)
- **Headline: original vs final** — display this pair inline; list every path so they can open any stage.

### Score progression
| Dimension | Iter1 | … | Final | Target |
(per-dimension rows + Overall)

### Changes applied
{changes_log grouped by iteration}

### Still below target (if MAX_REACHED)
{dims still < target, with remaining fixes}

### Rollback
- Git: `git log --oneline` then revert/reset to a checkpoint.
- Non-git: restore from `.design-backups/iter-N/`.
```

## Whole-site consistency (the real 整体质感)

Premium feel is a property of the **whole site**, not one page — a gorgeous homepage bolted onto a generic inner page reads as *less* premium than a consistent, slightly-less-flashy whole. This skill's runs are otherwise islands, so:
- Put the design language in **shared globals + tokens** (type scale, colours, radii, shadows, the light/motion system, the card recipe) — not inline on one page — so other pages inherit it.
- Asked to polish another page later → **reuse the established system**, don't invent a parallel one.
- Offer a quick **cross-page consistency audit**: same header/nav, card/shadow/radius vocabulary, motion language, type scale. Inconsistency *between* pages is itself a premium-killer the single-page loop never sees.

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Scoring from source when chrome was available | Always probe; render and look first. |
| Adds flashy motion and leaves it | Law 2: every motion add gets a "more subtle, more refined" tame pass. |
| "Responsive = mobile done" | Resizing isn't designing — do the dedicated mobile pass. |
| Adding sections/elements to look richer | Premium is restraint; refine, don't add. (But don't suppress richness the user *asked* for.) |
| Skipping the checkpoint | No checkpoint = no rollback. Never skip. |
| Encouraging, vague scores | Reviewer must be honest + cite specifics, or nothing gets fixed. |
| "Rewrite freely" on a large in-use tool | Safe-layer-first; never touch logic; confirm structural changes (product decisions). |
| Tuning motion through the score loop | Motion can't be scored from a still — tune live via knobs. |
| Leaving generic Inter in place | Swap it (Law 3) unless font-swap is off. |

## Red Flags — stop and correct

- About to score colour/motion/mobile without ever rendering → render first.
- About to edit before checkpointing → checkpoint first.
- Looping after all dims pass, OR exiting on the cap before this round ever optimized → wrong; cap is checked in 3.6 after optimize+re-score.
- An edit you can't trace to a low-scoring dimension → scope creep; drop it.
- Premium direction conflicts with the brand's identity (mascot vs serious, warm vs cool, serif vs geometric, tech vs cozy, the existing palette/voice) → **STOP and surface the fork as the user's choice; never unilaterally rebrand.** These identity calls recur — each is a checkpoint, not an optimize step.
