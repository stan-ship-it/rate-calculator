# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file, static fee calculator for Google Ads media budgets, built for Moonshot Growth. The UI is in French.

**To run**: Open `rate_calculator.html` directly in any modern browser — no build step, server, or dependencies required.

## Architecture

Everything lives in a single file: `rate_calculator.html`. It contains embedded CSS (`<style>`) and JavaScript (`<script>`). The main design uses the shared Moonshot design system (`../main-design-system/` — tokens.css, base.css, components.css) and GSAP for animations.

### Easter Egg

The previous design (blue theme, rounded corners, Syne/Space Mono/JetBrains Mono fonts) is hidden as an easter egg, accessible via the Konami code (↑↑↓↓←→←→BA). It is fully self-contained within `#oldDesign` with scoped styles.

### Studio (V2)

The Studio design variant has been disabled/removed.

### Pricing Logic (`compute(budget)`)

Fixed base fee + tiered progressive model:

| Budget bracket | Rate |
|---|---|
| 0 – 5 000 € | 1 000 € forfait (flat fee) |
| 5 000 – 20 000 € | 15% |
| 20 000 – 50 000 € | 12% |
| 50 000 – 100 000 € | 10% |
| 100 000 €+ | 8% |

The first 5 000 € always costs a flat 1 000 €. Amounts above 5 000 € are charged at the progressive tiered rates.

`render(budget)` drives all UI updates: the three summary cards (fees HT, effective rate, total client cost), the bracket breakdown table, and the progress bar.

### Input UX

The number input and the range slider (0–150 000 €) are kept in sync via event listeners. Formatting uses `Intl.NumberFormat` with French locale (`fr-FR`).

## Frontend Design Philosophy

You tend to converge toward generic, "on distribution" outputs. In frontend design, this creates what users call the "AI slop" aesthetic. Avoid this: make creative, distinctive frontends that surprise and delight. Focus on:
 
Typography: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics.
 
Color & Theme: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes. Draw from IDE themes and cultural aesthetics for inspiration.
 
Motion: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions.
 
Backgrounds: Create atmosphere and depth rather than defaulting to solid colors. Layer CSS gradients, use geometric patterns, or add contextual effects that match the overall aesthetic.
 
Avoid generic AI-generated aesthetics:
- Overused font families (Inter, Roboto, Arial, system fonts)
- Clichéd color schemes (particularly purple gradients on white backgrounds)
- Predictable layouts and component patterns
- Cookie-cutter design that lacks context-specific character
 
Interpret creatively and make unexpected choices that feel genuinely designed for the context. Vary between light and dark themes, different fonts, different aesthetics. You still tend to converge on common choices (Space Grotesk, for example) across generations. Avoid this: it is critical that you think outside the box!