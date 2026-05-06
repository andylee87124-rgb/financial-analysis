---
name: financial-analysis
description: >
  Perform comprehensive financial analysis on companies, portfolios, or financial data.
  Use this skill whenever the user asks about financial statements, ratio analysis, 
  valuation, DCF modeling, equity research, stock screening, earnings analysis, 
  balance sheet review, income statement breakdown, cash flow analysis, financial 
  forecasting, or investment thesis development. Also trigger for requests involving 
  comparisons of financial metrics across companies, sector analysis, or any task 
  requiring structured financial output like a tearsheet, financial model, or 
  investment summary. If numbers, companies, and money are involved in an analytical 
  context, use this skill.
---

# Financial Analysis Skill

A comprehensive skill for performing rigorous financial analysis, valuation, and 
investment research with structured, professional-grade outputs.

---

## Core Capabilities

1. **Financial Statement Analysis** — Income statement, balance sheet, cash flow statement
2. **Ratio Analysis** — Profitability, liquidity, solvency, efficiency, valuation multiples
3. **Valuation Models** — DCF, comparable company analysis (comps), precedent transactions
4. **Earnings Analysis** — EPS, beat/miss, guidance, revisions
5. **Sector / Peer Benchmarking** — Cross-company metric comparison
6. **Investment Thesis** — Bull/bear case, risks, catalysts
7. **Financial Modeling** — Forecasting, sensitivity analysis, scenario analysis

---

## Workflow

### Step 1: Understand the Request

Identify what the user needs:
- Is this about a **specific company** (e.g., "analyze Apple's financials")?
- Is this about a **portfolio or sector** (e.g., "compare fintech valuations")?
- Is this a **modeling task** (e.g., "build a DCF for Tesla")?
- Is this **data-driven** (user uploads CSV/Excel) or **knowledge-based**?

If the user uploads a file (Excel, CSV, PDF), load and parse it first.

### Step 2: Gather Data

**For knowledge-based requests:**
- Use web search to find the latest financial data, SEC filings, earnings reports
- Search for: `[company] financial statements [year]`, `[company] 10-K`, `[company] earnings`
- Cross-reference multiple sources (SEC EDGAR, Yahoo Finance, company IR pages)

**For uploaded data:**
- Parse the file using Python (pandas for CSV/Excel, pdfplumber for PDFs)
- Validate data integrity before analysis

### Step 3: Compute Key Metrics

Always calculate the relevant metrics for the analysis type. See the reference tables below.

### Step 4: Structure the Output

Choose the appropriate output format based on complexity:
- **Quick analysis** → Conversational response with key metrics highlighted
- **Detailed report** → Word document (.docx) using the docx skill
- **Financial model** → Excel spreadsheet (.xlsx) using the xlsx skill
- **Presentation** → PowerPoint (.pptx) using the pptx skill

---

## Key Financial Metrics Reference

### Profitability
| Metric | Formula | Benchmark |
|--------|---------|-----------|
| Gross Margin | (Revenue - COGS) / Revenue | Industry-specific |
| EBITDA Margin | EBITDA / Revenue | >15% generally healthy |
| Net Profit Margin | Net Income / Revenue | >10% generally healthy |
| ROE | Net Income / Shareholders' Equity | >15% strong |
| ROA | Net Income / Total Assets | >5% solid |
| ROIC | NOPAT / Invested Capital | vs. WACC (>WACC = value creation) |

### Liquidity & Solvency
| Metric | Formula | Benchmark |
|--------|---------|-----------|
| Current Ratio | Current Assets / Current Liabilities | >1.5x healthy |
| Quick Ratio | (Cash + AR) / Current Liabilities | >1.0x |
| Debt/Equity | Total Debt / Equity | <2x for most industries |
| Net Debt/EBITDA | Net Debt / EBITDA | <3x generally comfortable |
| Interest Coverage | EBIT / Interest Expense | >3x |

### Valuation Multiples
| Metric | Formula | Notes |
|--------|---------|-------|
| P/E | Price / EPS | Compare to sector avg & historical |
| EV/EBITDA | Enterprise Value / EBITDA | Capital structure-neutral |
| EV/Revenue | Enterprise Value / Revenue | For high-growth or unprofitable cos |
| P/B | Price / Book Value | Useful for financials |
| PEG | P/E / EPS Growth Rate | <1.0 may indicate undervaluation |
| FCF Yield | Free Cash Flow / Market Cap | >5% attractive |

### Growth Metrics
| Metric | Formula |
|--------|---------|
| Revenue CAGR | (End Revenue / Start Revenue)^(1/n) - 1 |
| EPS Growth | (Current EPS / Prior EPS) - 1 |
| Rule of 40 (SaaS) | Revenue Growth % + EBITDA Margin % ≥ 40 |

---

## DCF Model Framework

When building a DCF:

1. **Project Free Cash Flows** (typically 5-10 years)
   - Revenue growth assumptions (conservative / base / bull case)
   - EBITDA margin trajectory
   - CapEx as % of revenue
   - Working capital changes
   - FCF = EBITDA - Taxes - CapEx - ΔWorking Capital

2. **Terminal Value**
   - Gordon Growth: TV = FCF_n × (1+g) / (WACC - g), where g = 2-3% long-term
   - Exit Multiple: TV = EBITDA_n × EV/EBITDA multiple

3. **Discount Rate (WACC)**
   - WACC = (E/V × Re) + (D/V × Rd × (1-T))
   - Re via CAPM: Rf + β × (Rm - Rf)
   - Use 10Y Treasury for Rf, 5-7% equity risk premium typical

4. **Intrinsic Value**
   - PV of FCFs + PV of Terminal Value = Enterprise Value
   - EV - Net Debt = Equity Value
   - Equity Value / Shares Outstanding = Intrinsic Value per Share

5. **Sensitivity Table**
   - Always show 3×3 or 5×5 sensitivity (WACC vs. terminal growth or exit multiple)

---

## Comparable Company Analysis (Comps)

1. Select 5-10 peer companies (same sector, similar size/growth profile)
2. Gather LTM (last twelve months) and forward metrics
3. Build a table with: Company, Market Cap, EV, Revenue, EBITDA, Net Income, key multiples
4. Calculate 25th / median / 75th percentile for each multiple
5. Apply median (or justified premium/discount) to subject company metrics
6. Triangulate with DCF

---

## Output Templates

### Quick Analysis Response Format
```
## [Company Name] Financial Snapshot

**Overview**: [1-2 sentence business description]

**Key Financials** (LTM or most recent fiscal year):
- Revenue: $X | YoY Growth: X%
- Gross Margin: X% | EBITDA Margin: X%  
- Net Income: $X | EPS: $X
- Free Cash Flow: $X

**Valuation**:
- Market Cap: $X | EV: $X
- P/E: Xx | EV/EBITDA: Xx | EV/Revenue: Xx
- vs. Sector Avg: [premium/discount]

**Balance Sheet Health**:
- Cash: $X | Total Debt: $X | Net Debt: $X
- Net Debt/EBITDA: Xx

**Assessment**: [3-5 sentence qualitative take on financial health, valuation, and key risks/opportunities]
```

### Investment Thesis Format
```
## Investment Thesis: [Company]

**Recommendation**: [Buy / Hold / Sell / Neutral]
**Target Price**: $X (upside/downside: X%)
**Time Horizon**: [X months/years]

**Bull Case** (weight: X%):
- [Catalyst 1]
- [Catalyst 2]

**Base Case** (weight: X%):
- [Assumption 1]
- [Assumption 2]

**Bear Case** (weight: X%):
- [Risk 1]
- [Risk 2]

**Key Metrics to Watch**:
- [Metric 1]: [threshold]
- [Metric 2]: [threshold]
```

---

## File Output Guidelines

- **Excel model requested** → Use the xlsx skill for multi-sheet financial models
- **Word report requested** → Use the docx skill for formatted equity research reports
- **Presentation requested** → Use the pptx skill for investor-style slide decks
- **Charts/visualizations** → Use Python (matplotlib/plotly) for standalone charts

When creating Excel financial models:
- Sheet 1: Assumptions & Drivers
- Sheet 2: Income Statement
- Sheet 3: Balance Sheet
- Sheet 4: Cash Flow Statement
- Sheet 5: Valuation (DCF + Comps)
- Sheet 6: Sensitivity Analysis

---

## Data Sources (for web search)

- SEC filings: `site:sec.gov [company] 10-K` or `edgar.sec.gov`
- Earnings: `[company] Q[X] [year] earnings results`
- Analyst estimates: `[company] consensus estimates [year]`
- Industry benchmarks: `[sector] average [metric] [year]`

---

## Important Caveats

Always include appropriate disclaimers:
- This is for informational/educational purposes only
- Not investment advice
- Past performance does not guarantee future results
- Verify data from primary sources (SEC filings, company IR) before making decisions

---

## Read These References When Needed

- `references/sector-benchmarks.md` — Typical metric ranges by industry sector
- `references/valuation-models.md` — Detailed modeling guidance (LBO, Sum-of-Parts, NAV)
