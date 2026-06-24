---
name: premium-design-loop
description: Use when improving a webpage's visual quality, craft, or "premium feel" — making a site look more expensive, high-end, and designed rather than generic or AI-made. Two modes: `Polish` (iteratively raise craft on the current design) and `Redesign`/leap (diverge to new concepts first, then polish the winner). Triggers include "make it look premium", "质感", "看起来更高级/更贵", "redesign / 重新设计 / 大改 / 太普通 / 不好看 / 太丑", scoring a site against premium design standards, iteratively polishing visual design, fixing the generic Inter-font AI look, doing a dedicated mobile pass, or adding tasteful micro-interactions. Works from a local code path and/or a reachable URL.
---

# Premium Design Loop

Iteratively evaluate and upgrade a webpage's craft. Each round: **checkpoint → score → optimize the weak dimensions → re-score**, until scores hit target or the iteration cap.

Core principle: **premium = finishing + intentional craft.** Every element earns its place through execution — depth, light, type, hierarchy, motion. Richness that serves the design is welcome; the bar is *intentional*, not *minimal*.

See **Light & Motion** below for how to add richness (light, motion, depth) that reads premium rather than cheap.

### Two ambition modes — pick one in Step 1

The scored loop is a **convergent hill-climber**: it polishes the *current* design's weak dimensions. That is the right engine for "make this good page great" — but it structurally **cannot leap to a different, better design**, because it never leaves the design it started on. A big visual jump needs *divergence* (invent several distinct directions), not more refinement of one.

- **`Polish`** — the existing convergent loop (Steps 1→2→3→4). Keeps the current layout/concept; raises craft. Use when the design is fundamentally right and just needs finishing.
- **`Redesign` (leap)** — run the **Re-envision phase (Step 2.5)** *first*: generate genuinely distinct design directions, let the user pick one, rebuild to it, *then* hand off to the convergent loop to polish the winner. **Redesign unlocks all THREE axes at once — macro-layout/information-architecture + palette/theme + the visual elements — not one at a time.** Changing only the element internals while keeping the same grid and the same colours is *partial* and still reads conservative. The *only* thing held fixed is the **data contract** (what data is shown + the events emitted) plus any brand essentials the user explicitly names (logo/mascot). **Everything else is on the table and should genuinely change.** Use when the page reads generic/template, when **Point of view scores low**, or whenever the user asks to "redesign / 大改 / 重新设计 / make it look completely different."

  **The engine is NOT a recipe for "good" — it is two repeatable moves: ① remove every constraint that isn't a true invariant, ② diverge widely.** There is no fixed definition of premium to converge toward; this doc's named techniques (genres, heroes, Sankey/gauges, "one accent", etc.) are *spent examples* — evidence the space is huge, **not a menu to pick from**. Each run should evolve something **different and better than last time** — do not reproduce the current page, a previous run's result, or the examples written here. If two runs converge on the same look, divergence failed.

**Default:** if the user says "polish / tidy / 微调 / fix X," use `Polish`. If they say "redesign / 重做 / 不好看 / 太普通 / make it premium from scratch," or POV is the lowest dimension, use `Redesign`. When unsure, ask (Step 1). Don't silently default to `Polish` for a page that needs a leap — that's the #1 way this skill underdelivers.

## When to Use

- A page (local path or URL) needs to look more high-end / premium / "expensive".
- A page reads as generic or obviously AI-generated (default Inter font, flat static sections, no finishing).
- A page needs a **bold leap / redesign**, not just polish ("太普通 / 不好看 / 重新设计 / 大改") — run `Redesign` mode (diverge to new concepts, then polish).
- You need an honest, scored design critique against a consistent rubric — then the fixes applied.
- A site "works on mobile" only by scaling down and needs a real mobile design pass.

**Not for:** building a page from scratch (use brainstorming/frontend-design first), pure copywriting, or backend work.

## The 12 Dimensions

Score each 1–10; "passing" = ≥ target (default **9**). All-12-at-9 is a high bar — most runs end `MAX_REACHED` with strong scores, which is a good outcome, not a failure.

| # | Dimension | What 9+ looks like |
|---|-----------|--------------------|
| 1 | Point of view | A clear opinion/aesthetic, not a template. Memorable, intentional. |
| 2 | Typography | Deliberate type scale, pairing, tracking, line-height. No default Inter look. |
| 3 | Colour | Intentional, coherent palette with real contrast hierarchy. No muddy defaults. (Bold/saturated or quiet — both can score 9; the bar is *intentional*, not *restrained*.) |
| 4 | Hierarchy | Eye lands where it should. Clear primary/secondary/tertiary. Intentional spacing rhythm — generous *or* dense, as the design demands. |
| 5 | Imagery | High-quality, consistent treatment (grade, crop, ratio). No stocky filler. |
| 6 | Motion | Intentional and controlled — motion *or* deliberate stillness serves the design; not accidental, janky, or distracting. (Subtle/eased is one valid register, not the only one; a chosen 光影=None / fully static design can still score 9.) |
| 7 | Mobile | Designed for small screens (hide/tighten/resize), not just scaled down. |
| 8 | Invisible finishing | Optical alignment, hover/focus states, empty states, radii/shadow consistency, micro-copy. |
| 9 | Accessibility | WCAG-level contrast, visible focus, keyboard nav, semantic markup, ARIA. |
| 10 | Performance | Fast first paint, optimized images, no jank, subset/preloaded fonts, no layout shift. |
| 11 | Design-system consistency | Spacing/size/radius/shadow come from tokens, not ad-hoc values. |
| 12 | Copy / microcopy | Has a voice and point of view. No generic AI filler ("Welcome to our website"). |

**The number is a loop-driver, not a metric.** Scores are subjective and inflate via anchoring (you feed prior scores in). Treat them as a rough "what to fix next / are we done" signal. The real deliverables are the **verdict text**, the **before/after visuals (+ GIF for motion)**, and the **user's eye**. Don't burn a re-score subagent on a tiny safe delta — state what changed and let the visual judge.

**Point of view (#1) is a gate, not 1/12.** The other 11 dimensions reward *refinement* — they climb with craft edits. POV rewards a *concept*, which craft edits can't produce; so the worst-dimension-first loop will keep fixing cheap craft and never touch POV, and the page stays a well-finished template. So: **if POV is below target, it is the worst dimension regardless of its number** — the prescribed fix is a *concept-level* move (re-layout, a hero, a new organizing idea), and in practice that means entering/re-entering **Re-envision (Step 2.5)**, never another typography/colour tweak. A page can score 8 on all 11 craft dims and still be a 6 overall because POV is a 5 — don't let the craft average hide that.

## The Craft Laws

The optimizer MUST honor these every round.

1. **Tame the first motion pass.** AI's first motion attempt is always too much. After adding motion, deliberately dial back: *"more subtle, more refined"* — slower easing, smaller travel, lower opacity deltas, lagged cursor-follow not instant snapping.
2. **Kill the generic AI font.** Default `Inter`/system sans = instant "AI-made" tell — swap for something with character. *Which* character is yours to invent; a self-hosted display woff2, or a serif-display + sans/mono-body pairing, is **one spent example, not the answer** — don't let every run default to the same pairing.
3. **Make stillness intentional, not accidental.** A flat section should read as a *choice*, not an oversight. If the design wants life, restrained micro-movement (parallax, hover reveals, subtle entrances) is *one* way — tasteful, eased, never carnival. But deliberate stillness is equally valid: if the user chose `光影=None`, or the concept is intentionally static, **do not add motion for its own sake.** Motion is a lever, not a requirement.
4. **Mobile is a design, not a resize.** Decide what to hide / tighten / reflow on small screens — don't just shrink.
5. **Tokenize the invisibles.** Spacing, radii, shadows, type sizes from one small scale. Fix optical alignment and hover/focus/empty states.

Prefer *intent* prompts ("this feels static and generic — make it more expensive with restrained cursor interaction") over micro-instructions, then tame with "more subtle, more refined."

**Premium baseline** — **fallback defaults for when nothing better is chosen; in `Redesign` these are spent examples to *beat*, not targets to hit.** Don't let them quietly pull every run toward the same look (all from tokens):
- **Type**: 4–5 sizes on a 1.2–1.33 ratio with a *big* jump to the display size — don't crowd 8 fuzzy sizes into a 10–18px band. Weight, not size, carries emphasis in dense UI. (Serif display + clean sans/mono body is *one* pairing, not the only one.)
- **Spacing**: 4/8px base, generous; let the hero breathe.
- **Colour**: e.g. one accent + a 4–5 step neutral ink ramp + semantic state colours. (A safe minimum — *not* a rule; "one accent" here is a spent example, not a cap on what a bold palette may do.)
- **Shadow**: soft, layered (`0 1px 2px` + `0 8px 24px` at 5–10%), never one harsh drop.
- **Radius**: a small fixed set (e.g. 6/10/14px).
- **Composition**: give the page a clear hierarchy and a point of view — the eye should land somewhere intentional, not skate across equal-weight tiles (the flat "template" tell). *One* way that works is leading with a hero + demoting the rest under one coherent voice — but that's a **fallback default, not the goal**; in `Redesign` invent a stronger organizing idea of your own rather than adopting this recipe.

## Light & Motion (光影) — premium vs cheap

The strongest premium lever **and** the easiest way to look cheap. It's not "motion > static" — both **intentional motion** and **intentional stillness** beat **accidental/bad motion**. Motion is a lever to reach for *when the design wants it* (and the user's 光影 level allows it), not a tax every page must pay; a deliberately still design is a legitimate premium choice.

| Premium motion | Cheap motion |
|---|---|
| Slow (300–800ms+), ease-out | Fast, bouncy, spin |
| Triggered by the user (cursor / scroll / hover) | Auto-loops that never stop |
| Subtle (small travel, low-opacity light) | Big travel, high contrast, attention-grabbing |
| Quiet while the user reads | Moving in the corner of the eye while reading |

**Deliver the richness the user picked.** If they chose a rich 光影 level or keep asking for "more / faster / add another," **deliver it** (kept slow + eased + reduced-motion-gated). Don't quietly shrink it back to "tasteful" against their wish.

**Toolkit — a vocabulary of *spent examples*, not a required menu** (honor the chosen 光影 level; invent your own light/motion language rather than defaulting to this list every run):
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
START → Configure (incl. ambition mode) → Probe environment
      → if Redesign: RE-ENVISION (Step 2.5) — diverge N concepts → user picks → rebuild to winner
      → LOOP[ checkpoint → shot(before) → score → all pass? EXIT
              : optimize weak dims → shot(after) + re-score → all pass? EXIT : cap reached? EXIT
              : plateaued + POV-capped? → re-enter RE-ENVISION (don't stop) : continue ]
      → Final report
```

The cap is checked **after** a full optimize+re-score (in 3.6), never before — else a low cap exits before any optimization runs. **The convergent loop polishes one concept; the leap comes from the Re-envision phase — entered up front in `Redesign`, or re-entered when craft plateaus (3.6).**

---

### Step 1 — Configure

> **MANDATORY CONFIG GATE — run this every single time, before Step 2 / Step 2.5 / any generator or builder subagent. No exceptions.** You MUST issue at least one `AskUserQuestion` covering the **required core set** below *each run*. **A value being "known" from earlier in the session, from project memory, or from a prior run does NOT exempt it — re-surface it and have the user confirm; never silently inherit/default the core set.** Convenience-inheriting the config is the #1 documented way this skill skips the user's voice (see Red Flags / Common Mistakes). If you're about to dispatch generators, rebuild, or enter the loop and you have NOT asked the core questions *this run*, STOP and ask first.

**Required core set (must be asked / confirmed every run):**
1. **Ambition mode** — `Polish` vs `Redesign`.
2. **Platform scope** — PC / Mobile / both.
3. **Design reference to FOLLOW** — "have a specific image/URL you want it to look like?" (yes → they send it; no → free).
4. **光影 level** + **Animation kinds** — always offer (defaults are a starting point the user can change, not a reason to skip the ask).

(Run-mode, target, fonts, extra-dims, craft-anchor: ask only if unclear / relevant; documented defaults are fine for these *non-core* items.)

`AskUserQuestion` allows **max 4 questions/call** — batch the core set across one or two calls. "State the documented defaults for the rest" applies ONLY to the non-core items above; it is **not** a licence to skip the core set. If the user pre-specified a core value *in this run's prompt*, you may pre-fill it as the recommended option but still show it for confirmation.

- **Ambition mode**: `Polish` vs `Redesign` (leap) — see *Two ambition modes* above. **This is the single biggest outcome lever — lead with it.** `Redesign` runs the Re-envision phase (Step 2.5) before the loop. Don't assume `Polish`.
- **Target**: local path and/or reachable URL. A path is required to apply fixes; a URL/local-serve to *see* rendering. URL-only → you can score but not fix (offer a one-pass score-only review, or ask for the path).
- **Run mode**: `Auto` (run all rounds, report at end) or `Step` (pause each round to confirm). Default `Step` for large in-use tools and for `Redesign` (the concept pick wants a human). **In `Auto`, never block mid-loop for a human decision — defer every interactive call to the final report:** motion gets one conservative first-pass (documented knob defaults, flagged *needs-live-tuning*); **Green-zone visual/layout changes are applied freely** (that's not a human decision); only **Red-zone edits (logic/state/data/contract/routes) and identity/concept forks** are *not* applied but collected into a **needs-confirmation list** (in `Redesign+Auto`, generate the directions but defer the *pick* to the report); a dirty working tree is handled by file-copy backup, not a stop. Auto runs the non-interactive work and reports the rest — it must not silently drop to Step or fake-wait for the user.
- **Max iterations**: default **5**. **Target score**: default **9**.
- **Swap generic fonts?**: default **yes**. **Extra dimensions** (a11y/perf/design-system/copy): default **all on**.
- **Platform scope**: `PC only` / `Mobile only` / `PC + mobile` (default **both**) — controls which viewports get shot/scored/optimized. Don't waste a viewport they didn't ask for.
- **Reference anchor(s)**: the brand/site whose premium feel to aim at (Apple, Linear, Stripe, Vercel, 無印良品, or a URL). **Ask, don't default.** Use it two ways, not one: (a) **generative** (esp. `Redesign`) — prompt *"design THIS page as if `<ref>`'s team owned it: what composition, type system, density, and light would they choose?"* so the reference produces a concrete alternative *layout*, not just a verdict; (b) **scoring** — reframes "abstract 9/10" → "as premium as `<ref>`?". Borrow the reference's *craft and compositional thinking*, never its literal layout or **identity** — keep the user's brand essentials (logo/mascot/voice). In `Polish` keep the palette too unless the user says otherwise; in `Redesign` the palette is one of the three axes in play (the user picks a new one at 2.5.3).
- **Design reference to FOLLOW** (image / screenshot / URL) — *distinct from the craft anchor above*. **Ask: "do you have a specific design (image or website) you want this page to look like?"** If yes, this is a **source to adapt**, not just a craft level to aim at: **extract its design language — layout/composition, palette, type system, spacing, density, motion, light — and rebuild the page in that language with our own data + named brand essentials.** Two uses, don't conflate:
  - *Anchor* (the bullet above): "as premium as Linear" → borrow craft, invent the layout.
  - *Source/template* (this one): "make it look like THIS" → reproduce its design language closely, mapping our data into its structures.
  A given source is a **user-chosen constraint that narrows divergence toward that language** — honouring it is *not* the conservative trap (the trap is the skill's *own* unrequested limits). In `Redesign`, directions then vary in *how* they interpret/adapt the source, not whether. Probe it in Step 2 (screenshot the URL / read the image); feed it to the Re-envision generators (2.5.2).
- **光影 level**: `None` / `Subtle` / `Medium` / `Rich` (default **Subtle–Medium**). **Still a first-class option — always offer it.**
- **Animation kinds** (multi-select): entrance · cursor parallax · hover micro-interactions · scroll reveal · ambient drift. Default **entrance + hover + subtle ambient**. (All slow/eased/reduced-motion-gated — see Light & Motion.)

### Step 2 — Probe environment

- **Rendering** (strongly preferred — makes colour/motion/mobile/finishing scores reliable). Probe for `claude-in-chrome` tools or a `chrome-devtools` MCP (`mcp__chrome-devtools__*`). If present → open target, screenshot desktop + a real mobile viewport.
  - **If no browser control, do NOT silently fall back to source-only** — interrupt with one `AskUserQuestion`. On confirm, enable one in a step:
    - **Claude in Chrome** (uses the user's real logged-in browser — best for gated/auth pages): install the extension (Chrome/Edge only) → `/chrome` in session. ⚠️ The Web Store extension must be added by the *user*; you can't install it. Walk them through, then re-probe.
    - **chrome-devtools MCP** (fresh browser, you install it): `claude mcp add chrome-devtools npx chrome-devtools-mcp@latest` (Node 22+, local Chrome). No saved logins.
    - **Skip → source-only (degraded)**: mark colour/motion/mobile/finishing `(inferred)`; offer to lower target to ~8 since a true 9 is unlikely without rendering.
  - Proceed source-only only if the user picks Skip (or, in `Auto`, doesn't answer — note it).
- **Locate the target, then serve it** (local path): a repo (e.g. `./web`) is usually **multi-route** — identify and confirm the specific route + source file to polish; don't assume `page.tsx` is the page they mean. Then serve: detect the framework → run its dev command (`npm run dev` etc.) → wait for the port → render the target route's URL.
- **Capture the design reference, if one was given** (the *source to follow* from Step 1): screenshot the URL (chrome) or Read the provided image, at the target viewport. Study its design language — layout/grid, palette (sample real values), type, spacing/density, motion, light — and hold it as the concrete source the rebuild adapts (used in 2.5.2 / applied in Polish too).
- **Backup**: git repo? → checkpoints are commits. Else → copy touched files into `.design-backups/iter-N/`.

State which modes are active before the loop.

### Step 2.5 — Re-envision (the leap; `Redesign` mode only)

This is the phase the convergent loop can't do for you: **diverge before you converge.** Skip it entirely in `Polish` mode. Run it when ambition = `Redesign`, or when 3.6 escalates here after a craft plateau.

1. **Checkpoint first** (3.1 rules) — a redesign edits more files than a polish round; back them up.
2. **Strip constraints, then diverge for variance.** Two moves, in order:
   - **(a) Constraint audit — strip to the true invariants.** Write down the *only* things that genuinely cannot change: the **data contract** (inputs each component receives + events it emits), **brand essentials the user explicitly named** (logo/mascot/voice), and the **a11y + quality gates** (contrast, lint/types/tests). **Everything else is a self-imposed limit** — the current layout, palette, components, density, the page's metaphor, even "is it a dashboard / a grid / this set of sections at all". List those assumptions explicitly and **drop them.** The recurring failure this skill exists to prevent is mistaking a habit ("keep the components", "keep the palette", "keep it reasonable for an ops tool") for a requirement. If you can't trace a limit to a true invariant above, it's removable — remove it.
   - **(b) Diverge — generate, don't critique; maximize variance.** Dispatch **2–3+ parallel `Task` generators**, each inventing *one* direction that re-decides the now-unlocked space — at least **layout/IA + palette + visual elements** together (changing only one axis is the conservative trap: new furniture in the same room/floor-plan/paint). **The goal is SPREAD, not a house style:** give each generator a deliberately different starting lens, push each to the edge of what the invariants allow, and **reject any direction that resembles the current page, a previous run, or another generator.** The concrete moves named anywhere in this doc — genres, a "verdict hero", Sankey/gauges/timelines, "one accent", "demote the rest" — are **spent examples, not a checklist**; a generator that lands on one of them has under-reached. Each direction still needs *some* organizing idea that gives it a point of view — but **invent that idea fresh**; it need not be a hero, a genre, or anything listed here. Feed each: the current screenshot (*the floor to beat*, not the anchor), the reference anchor used *generatively* (Step 1), **the design reference to follow if one was given (the captured image/site from Step 2) — directions then adapt ITS language (layout/palette/type/motion) to our data and vary in *how* they interpret it, not *whether***, the named brand essentials, and **the data contract that must survive — NOT the current markup/layout/colours.** Each returns: a one-line concept, its organizing idea, the new layout/IA, new palette, new visual element per data type, type/motion moves, and *why it's premium and unlike the others*. Render a quick static mockup per direction when feasible.
3. **Select — the user's call.** Present the directions side by side (use `AskUserQuestion` with `preview` mockups/ASCII), each showing its organizing idea + layout + palette + key elements. **The user's pick IS their consent to that direction's palette/identity shift** — so a Redesign that changes colours is not a unilateral rebrand, it's a chosen one. Never pick for them; but once picked, apply the new palette fully (don't get cold feet and keep the old colours). **When ranking / recommending directions** (and when *autonomous* with no user to pick): favour the one with the **most distinct, committed point of view** and the **biggest departure from the current design** — and be *suspicious of the direction that most resembles the status quo* (same skeleton / same palette family / the current page lightly restyled): that's the conservative trap re-entering wearing a "redesign" label. Boldest-coherent beats safest-familiar — but "coherent" is each direction's own internal logic, not conformance to any house recipe.
4. **Rebuild to the winner — change layout + palette + elements together; don't half-do it.** Apply it as a **bold first pass**. The hard constraint is narrow: **preserve the DATA CONTRACT — the inputs each component receives and the events it emits (`props`/`emit`/data/routes)** + named brand essentials. Everything else is fair to throw away and rebuild:
   - **Layout/IA** — re-author the container (`DashboardView`/page root): new grid or scene, merge/drop/demote sections per the chosen direction. Don't keep the old skeleton.
   - **Palette** — apply the chosen new theme (redefine the colour tokens — globally if the user allowed, or scoped to the page if they said page-only).
   - **Visual elements** — rewrite component internals or write brand-new presentational components so the same data prop renders as the new element (Sankey / gauge / timeline).
   **Half-doing it — new elements inside the old layout and old palette — is the exact failure that keeps reading "conservative".** Do all three. Front-load the boldness; tame later. Verify it still renders (3.4 render check) + checkpoint.
5. **Hand to the loop.** Now enter Step 3 to polish the chosen direction's craft. The leap happened here; the loop makes it premium.

Expect to land somewhere bolder than any polish round could reach. If all directions feel timid, the generators were under-briefed — re-dispatch with "the current page is the floor, not the anchor; propose what you'd ship to win a design award."

### Step 3 — The Loop

Maintain across iterations: `iteration`, `scores_history`, `changes_log`, `target_score`, `max_iterations`.

**3.1 Checkpoint (before any edit) — MANDATORY BACKUP GATE.** **Back up the previous design before ANY modification, every round, every run — and every subagent must do the same before it edits.** This is a hard gate, not a suggestion: **never modify a style/component/token file you have not first copied this round.** **Default to the file-copy backup** — copy the target page's files + the styles you're about to touch (views/components + shared CSS/tokens) into `.design-backups/iter-N/` (widen if a later edit touches more). It sidesteps two real traps: you don't yet know which files this round edits (that's decided in 3.4), and the working tree is often already dirty with the user's unrelated changes. Use a **git-commit** checkpoint *only* if the tree is clean and the user prefers it (`git add <target files>` — never `git add -A`; no `--no-verify`). **In `Auto`, never stop to ask about a dirty tree** — the file-copy backup makes it safe. Add `.design-shots/` + `.design-backups/` to `.gitignore`. **Never skip — the prior styles are the user's only rollback;** when dispatching a builder/generator subagent, instruct it to back up first too (and confirm it did). Re-envision has its own copy of this rule at 2.5.1.

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

**3.4 Optimize (apply edits).** Worst dimension first — **but treat a below-target POV as the worst dimension** (see the POV gate) and route it to Re-envision (Step 2.5), not a craft tweak. Otherwise apply the reviewer's `fixes` under the Craft Laws (swap fonts; tame motion; dedicated mobile pass; add restrained interaction to static/flat sections).
- **Surgical = no *unrelated* changes — not "small" changes.** In `Polish`, every edit traces to a low-scoring dimension. In `Redesign`, the *whole composition* is the thing being changed — a large layout rewrite traces to POV/Hierarchy and is correct; don't shrink it back to tweaks. Either way: don't touch code unrelated to the design.
- **Scope by RISK to data/logic, not by visual ambition** (this replaces the old "safe-layer-first / confirm every structural change" rule, which throttled every real app down to CSS tweaks). The real invariant on a working tool is: **preserve data wiring, state, and the component contract (`props`/`emit`/inputs/outputs/routes).** With those held, **visual structure — layout, composition, hierarchy, what's hero, how sections nest — is fair game**, including in `Redesign`. Concretely:
  - **Green (just do it):** re-authoring the page container's **layout / information-architecture** (new grid or scene, merge/drop/demote sections); the **palette / colour theme** (redefining colour tokens — once chosen, see below); type/spacing/radius/shadow tokens, hover/focus/empty states, a11y/contrast; **and rewriting a presentational component's internals or replacing it with a brand-new visualisation that renders the same data prop** (node-diagram → Sankey, cards → gauges, list → timeline). In `Redesign` all three axes (layout + palette + elements) are Green together. The data contract is the boundary, not the existing markup/layout/colours. Bold visual change doesn't need per-edit sign-off.
  - **Red (never without explicit ask):** editing business logic, state, data flow, API/query shapes, or the props/emit contract; deleting features or data; rewiring routes/nav targets. Use grep + scoped edits; checkpoint every round.
  - **Identity fork (a *one-time* user choice, then Green):** changing brand identity (warm↔cool, serif↔geometric, palette/mascot/voice). In `Polish` surface it as a fork and don't move unilaterally. In `Redesign` it's already decided by the direction the user picked (2.5.3) — apply it fully. Scope of the palette change (global tokens vs page-scoped) follows what the user said about scope.
  - Reweight the rubric for dense tools — density, scan path, cell/row alignment outweigh imagery/copy — but that reweighting is *not* a licence to avoid the leap.
- **Verify it still renders before scoring.** Reload after editing (esp. TSX/JS) — a bad edit can blank the page or throw. A broken render is an auto-fail, not a low score; check the console. **A passing dev render ≠ a passing production build** — a type error can blank prod while dev only shows an overlay; run a typecheck/build before declaring done or deploying.
- Record each change in `changes_log`.

**3.5 Capture "after" shots + re-score.** Re-shoot to `.design-shots/iter-N/after-{desktop,mobile}.png`. Re-run the 3.2 reviewer on the after-state, passing this round's opening scores + `changes_log` so it judges whether each weak dim improved. These **closing scores** are the round's result → append to `scores_history`, carry forward as next round's opening.

**3.6 Pass + cap + plateau gate.** Closing scores all ≥ target → `SUCCESS`. Else `iteration >= max` → `MAX_REACHED`.

**Plateau → escalate, don't park.** If a round improved no dimension by ≥1 (craft has plateaued), the craft ceiling on *this concept* is reached. That is the signal to **leap, not to stop** — because "all craft dims ~8 but it still doesn't wow" means the limit is the concept itself:
- **If POV is below target (or the page still reads generic / the user isn't happy):** enter **Re-envision (Step 2.5)** — diverge to a new concept — instead of reporting done. Craft-maxed-but-flat is exactly when the leap pays off; the old "stop early" brake fired here and was the main reason this skill underdelivered.
- **Only genuinely stop** when POV is already at target *and* the remaining gaps need things a craft round can't supply — external assets (real imagery/illustration), an explicit product decision, or a **live motion-tuning pass** (motion can't be scored from a still; hand off to the knob-loop). Report those as next steps, don't fake-iterate.

Otherwise: `Auto` → loop to 3.1. `Step` → show opening→closing delta + edits, confirm before next round (offer the Re-envision leap explicitly when plateaued); if user stops → `PAUSED`.

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
| Skipping the Step-1 config questions because values seem "known" from the session / memory / a prior run | Standing values do NOT exempt the core set — run the **mandatory config gate** (ambition · platform · design-reference-to-follow · 光影/animation) every run; confirm, don't silently inherit (Step 1). |
| Scoring from source when chrome was available | Always probe; render and look first. |
| Adds flashy motion and leaves it | Law 1: every motion add gets a "more subtle, more refined" tame pass. |
| "Responsive = mobile done" | Resizing isn't designing — do the dedicated mobile pass. |
| Skipping the backup / editing un-backed-up styles (incl. inside a subagent) | Mandatory backup gate (3.1): copy the previous styles/components/tokens to `.design-backups/iter-N/` before ANY edit, every round; tell subagents to do the same. No backup = no rollback. |
| Encouraging, vague scores | Reviewer must be honest + cite specifics, or nothing gets fixed. |
| Throttling a working app down to CSS tweaks "to be safe" | Scope by *risk to data/logic*, not visual ambition (3.4): preserve props/emit/state/data; layout & composition are fair game. |
| Polishing a page that actually needs a new concept | Use `Redesign` + Re-envision (Step 2.5); don't hill-climb a template forever. |
| "Redesign" that only changes ONE axis (new elements in the old layout + old palette, or just a re-grid) | Half-done = still reads conservative. Redesign changes all three — layout/IA + palette + elements — together (2.5.2/2.5.4). Only the data contract is fixed. |
| Keeping the old palette in a Redesign "to be safe" | Palette change is part of the leap; the user's direction-pick is consent. Apply the new theme fully — don't get cold feet (2.5.3). |
| Equal-weight tiles / blocks — reads flat & template | Give it a clear point of view + hierarchy (one *option*: a hero + demotion — not mandatory). |
| Picking the "safe" direction that resembles the current design | Favour most-distinct-POV + biggest-departure; distrust the status-quo lookalike (2.5.3). |
| Treating this doc's example moves (genres / verdict-hero / Sankey / "one accent") as a recipe → every run converges to one house style | They're *spent examples*, not a checklist. Diverge past them; each run should land somewhere they don't name (2.5.2). |
| Mistaking a habit for a requirement ("keep the components / palette / make it reasonable") | Run the constraint audit (2.5.2a): only data-contract + named brand + a11y/quality are invariant; drop the rest. |
| Stopping when craft plateaus but it still doesn't wow | Plateau = leap signal (3.6) — re-enter Re-envision, don't report "done". |
| Only critiquing, never generating alternatives | Re-envision uses *generator* subagents that invent distinct concepts, not just critics that suggest fixes. |
| Tuning motion through the score loop | Motion can't be scored from a still — tune live via knobs. |
| Leaving generic Inter in place | Swap it (Law 2) unless font-swap is off. |

## Red Flags — stop and correct

- About to dispatch generators / rebuild / enter Step 2.5 or the loop **without having asked the Step-1 config core set this run** → STOP; run the mandatory config gate first (ambition · platform · design-reference-to-follow · 光影/animation). Session/memory "standing config" is not consent — re-confirm.
- About to score colour/motion/mobile without ever rendering → render first.
- About to modify ANY style/component/token file (yourself or via a subagent) without having backed up its previous version this round → STOP; copy it to `.design-backups/iter-N/` first. The prior styles are the user's only rollback (3.1 mandatory backup gate).
- Looping after all dims pass, OR exiting on the cap before this round ever optimized → wrong; cap is checked in 3.6 after optimize+re-score.
- In `Polish`, an edit you can't trace to a low-scoring dimension → scope creep; drop it. (In `Redesign`, a whole-composition rewrite traces to POV/Hierarchy — that's the point, not scope creep.)
- Editing business logic / state / data flow / props·emit contract / routes to chase a visual fix → STOP; that's the Red zone (3.4). Visual structure is fair game; data wiring is not.
- Craft plateaued and you're about to report "done" while the page still reads generic / POV is below target → wrong; escalate to Re-envision (3.6), don't park.
- In `Redesign`, only one axis is actually changing (new elements but the SAME layout + SAME palette, or a re-grid with the same components) → STOP; that's the conservative trap. Change layout/IA + palette + elements together (2.5.4). Only the data contract is sacred.
- Defaulting to `Polish` for a page the user called generic / "太普通 / 不好看 / redesign" → wrong mode; that's a `Redesign`/leap.
- Premium direction conflicts with the brand's identity (mascot vs serious, warm vs cool, serif vs geometric, tech vs cozy, the existing palette/voice) → **in `Polish`, STOP and surface the fork as the user's choice; never unilaterally rebrand.** In `Redesign` this fork is resolved *by the direction the user picked* in Step 2.5.3 — that pick is consent, so apply the new palette/identity fully rather than re-blocking it. The guard is against *unilateral* rebrand, not against a *chosen* one.
