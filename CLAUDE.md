# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file, static fee calculator for Google Ads media budgets, built for Moonshot Growth. The UI is in French.

**To run**: Open `rate_calculator.html` directly in any modern browser — no build step, server, or dependencies required.

## Architecture

Everything lives in a single file: `rate_calculator.html`. It contains embedded CSS (`<style>`) and JavaScript (`<script>`), with no external dependencies beyond Google Fonts.

### Pricing Logic (`compute(budget)`)

Tiered progressive fee model with a 800€ minimum:

| Budget bracket | Rate |
|---|---|
| 0 – 5 000 € | 18% |
| 5 000 – 20 000 € | 15% |
| 20 000 – 50 000 € | 12% |
| 50 000 – 100 000 € | 10% |
| 100 000 €+ | 8% |

`render(budget)` drives all UI updates: the three summary cards (fees HT, effective rate, total client cost), the bracket breakdown table, and the progress bar.

### Input UX

The number input and the range slider (0–150 000 €) are kept in sync via event listeners. Formatting uses `Intl.NumberFormat` with French locale (`fr-FR`).
