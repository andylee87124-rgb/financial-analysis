# Advanced Valuation Models

## 1. Leveraged Buyout (LBO) Analysis

Use when: Evaluating private equity acquisition potential, or assessing how a company could be taken private.

### Key Inputs
- Entry EV / Entry EBITDA multiple
- Debt/EBITDA at entry (leverage)
- Debt tranches: Senior secured (3-4x), Total (5-6x typical)
- Revenue growth, margin expansion assumptions
- Exit multiple and year (typically 5-year hold)
- Management fees, transaction costs

### LBO Return Drivers
1. **Multiple expansion** — buy at 8x, sell at 10x
2. **Earnings growth** — EBITDA grows, equity value grows
3. **Debt paydown** — leverage paid down from cash flows

### IRR Benchmarks
- <15%: Below hurdle for most PE funds
- 20-25%: Solid return
- 25%+: Strong deal

### Quick LBO Sketch
```
Entry Equity = Entry EV - Debt at Entry
Exit EV = Exit EBITDA × Exit Multiple
Exit Equity = Exit EV - Remaining Debt
IRR = (Exit Equity / Entry Equity)^(1/hold years) - 1
MOIC = Exit Equity / Entry Equity
```

---

## 2. Sum-of-Parts (SOTP) Valuation

Use when: Conglomerate or multi-segment companies where divisions have different business models / peer multiples.

### Process
1. Identify distinct business segments
2. Assign appropriate valuation methodology per segment (DCF, EV/EBITDA comps, etc.)
3. Value each segment independently
4. Sum segment values → Total Enterprise Value
5. Subtract net debt, minority interest → Equity Value
6. Apply holdco discount if applicable (10-20% typical)

### SOTP Table Template
| Segment | Revenue | EBITDA | Multiple | Segment EV |
|---------|---------|--------|----------|-----------|
| Segment A | $X | $X | Xx | $X |
| Segment B | $X | $X | Xx | $X |
| Corporate | — | -$X | Xx | -$X |
| **Total EV** | | | | **$X** |
| (-) Net Debt | | | | -$X |
| **Equity Value** | | | | **$X** |

---

## 3. Net Asset Value (NAV)

Use when: Asset-heavy companies — REITs, E&P oil/gas, holding companies, mining.

### Real Estate NAV
1. Value each property: NOI / Cap Rate = Property Value
2. Sum all property values → Gross Asset Value
3. Subtract total liabilities → NAV
4. NAV per share = NAV / Shares Outstanding
5. Compare to market price → Premium/Discount to NAV

### E&P NAV
1. Engineer reserve report (1P, 2P, 3P reserves)
2. Risked NPV10 of each reserve category
3. 1P + 50% 2P + 20% 3P (typical risking)
4. Add net cash, subtract debt → Equity NAV

---

## 4. Dividend Discount Model (DDM)

Use when: Mature, stable dividend-paying companies (utilities, REITs, telecoms, banks).

### Two-Stage DDM
- Stage 1: Explicit dividend forecast (5 years)
- Stage 2: Gordon Growth terminal value

```
Value = Σ [Dt / (1+r)^t] + [D_n+1 / (r - g)] / (1+r)^n

Where:
r = required return (cost of equity)
g = perpetual dividend growth rate (typically GDP growth ~2-3%)
```

### Inputs
- Current dividend per share
- Dividend growth rate (stage 1 and terminal)
- Cost of equity (CAPM)

---

## 5. EV/EBITDA Regression (Intrinsic Multiple)

Use when: Deriving a "fair" multiple based on fundamentals rather than peer observation.

Key drivers of EV/EBITDA:
- Growth (higher growth → higher multiple)
- Margin quality (higher quality → higher multiple)  
- Capital intensity (lower CapEx → higher multiple)
- Balance sheet risk (higher leverage → lower multiple)

Regression framework:
```
EV/EBITDA = α + β₁(Revenue Growth) + β₂(EBITDA Margin) + β₃(CapEx/Revenue) + β₄(Net Debt/EBITDA)
```

Run this regression on comps set to derive implied multiple for subject company.

---

## 6. Scenario Analysis Template

Always present 3 scenarios for any valuation:

| Assumption | Bear | Base | Bull |
|-----------|------|------|------|
| Revenue Growth | X% | X% | X% |
| EBITDA Margin | X% | X% | X% |
| Exit Multiple | Xx | Xx | Xx |
| WACC / Discount Rate | X% | X% | X% |
| **Intrinsic Value** | **$X** | **$X** | **$X** |
| **Upside / Downside** | X% | X% | X% |
| Probability Weight | 25% | 50% | 25% |
| **Weighted Value** | | **$X** | |
