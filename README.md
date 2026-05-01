# Finance Manager

## Overview
A personal finance management application that helps users track income, expenses, and financial health over time. You can set your income and add transactions and it will show a chart that track spending vs. savings across the last 6 months. All data persists using localStorage.

## How to Run
- Clone the repo and open `index.html` in any browser
- No installs needed

## Tech Stackis 
- **HTML5, CSS3, Vanilla JavaScript** — single file architecture
- **Chart.js** — pie and bar charts
- **localStorage** — data persistence per month

## Architecture
Everything lives in one `index.html` file with CSS in `<style>`, JavaScript in `<script>`. Data is stored with specific month keys so each month has independent data. Core functions: `setIncome`, `addTransaction`, `deleteTransaction`, `updateSummary`, `updateChart`, `updateMonthlyChart`, `saveToLocalStorage`, `loadFromLocalStorage`.

## AI Tools Used
- **Tool:** Claude (claude.ai)
- **How I used it:** Scaffolded HTML structure, explained some unfamiliar JavaScript concepts relative to my Java/Python background, debugged a variable shadowing bug in `setIncome()`, and helped design the per-month localStorage architecture
- **Prompts that worked well:** Asking for line-by-line explanations and Java/Python comparisons before moving forward

## Key Design Decisions
- **Single file:** Simple because having separate files would add complexity without benefit
- **No framework:** Plain JavaScript keeps every line explainable
- **Per month localStorage keys:** Allows monthly tracking
- **Categories based on Sofi and WalletHub reference resources** provided in the brief

## Challenges & How I Solved Them
- **Variable shadowing:** `let income` inside `setIncome()` created a local variable, so global income never updated. Removing `let` fixed it.
- **Load order bug:** Loading transactions before income caused wrong net savings on reload. Fixed by loading income first, then calling `updateSummary()` once at the end.
- **Overlapping charts:** Solved by calling `window.myChart.destroy()` before rendering a new chart.

## What I'd Improve With More Time
- **Clear month button** using `localStorage.removeItem()` with a `confirm()` dialog
- **50/30/20 rule indicator** showing how spending compares to typical guidelines
- **Edit transactions** instead of delete and re-add