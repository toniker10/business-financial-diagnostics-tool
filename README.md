# Business Financial Diagnostics Tool

An interactive Python tool that works like a **pocket financial advisor** for small businesses. It asks simple, guided questions (no accounting background needed), calculates revenue, profit, break-even, cash-flow risk and liquidity ratios, and ends with a prioritised action plan: what to fix first.

|            |                                                                              |
|------------|------------------------------------------------------------------------------|
| **Role**   | Data analyst (portfolio project)                                             |
| **Tools**  | Python 3, matplotlib, JSON (standard library otherwise)                      |
| **Input**  | Answers typed by the business owner (costs, products, staff, cash, debts)    |
| **Output** | Console report, text report, 3 charts, history file for month-over-month use |

The report follows four steps: **What** happened, **Why** it happened, **So what** it means, **Now what** to do.

---

## Example run

> **Note:** the inputs below are illustrative sample numbers for a small bar, not a real business. The tool's calculations are real.

Inputs: 3 products (coffee €5.00, juice €3.00, beer €6.00; 1,000 / 2,000 / 4,000 sold per month), €3,000 fixed costs, 3 employees (€2,402 payroll).

### 1. What (what the numbers show)

| Metric                     | Result       |
|----------------------------|-------------:|
| Revenue                    | 35,000       |
| Total costs                | 12,802       |
| Profit (pre-tax)           | 22,198       |
| Break-even revenue         | 6,850        |
| Bankruptcy risk score      | 36.6 / 100   |
| Combined risk level        | Low          |
| Business Health Score      | 78.1 / 100   |

The business sells about five times its break-even level, so it has an 80% margin of safety.

### 2. Why (what explains it)

| Product | Margin | Monthly profit contribution |
|---------|-------:|----------------------------:|
| Beer    | 83.3%  | 20,000                      |
| Coffee  | 80.0%  | 4,000                       |
| Juice   | 60.0%  | 3,600                       |

- **Beer drives the result:** it brings in 69% of revenue and 72% of the profit contribution.
- **Costs are light:** payroll is about 7% of revenue and fixed costs are 3,000, so most of each sale is kept.

### 3. So what (what it means)

- The business is healthy, but it depends on one product. A 20% fall in beer sales would remove about 4,000 of monthly profit.
- The what-if scenarios show it can absorb shocks:

| Scenario                  | Monthly profit |
|---------------------------|---------------:|
| Current                   | 22,198         |
| All prices +10%           | 25,698         |
| Sales -20%                | 16,678         |
| Product costs +15%        | 21,088         |

- Even in the worst case (sales -20%) the business stays clearly profitable.

### 4. Now what (what to do)

| # | Action                                                                                               | Success metric                         |
|---|------------------------------------------------------------------------------------------------------|----------------------------------------|
| 1 | Push the best earner (beer): feature it on the menu and bundle it. +10% beer sales is worth ~2,000/month | Beer units sold per month              |
| 2 | Test a small price rise before applying it to everything (+10% prices adds ~3,500/month in the model, but demand may drop) | Units sold after the change            |
| 3 | Watch the dependence on beer; promote coffee and juice so a bad beer month hurts less                | Beer share of revenue (now 69%)        |
| 4 | Re-run monthly, and use the history file to see what improved and what got worse                     | Health score and profit vs last month  |

These actions are the Business Doctor's output (action 1) plus the analyst's reading of the results (actions 2-4).

---

## What it does

The tool walks the owner through the business step by step.

**Collects the numbers**
- Fixed monthly costs, entered one item at a time (rent, utilities, subscriptions)
- Each product: selling price, cost to make one unit, units sold per month
- Employees and employer contributions
- Suppliers, with a warning against double-counting costs already in the product data
- Cash reserve
- Optional: VAT/sales tax, card or delivery-platform fees, waste, equipment depreciation
- Liquidity snapshot: unpaid supplier invoices, short-term debts, receivables, inventory

**Diagnoses the business**
- Revenue, costs and profit/loss, broken down per product and per supplier
- Break-even revenue
- Cash-flow runway: how many months the reserve lasts if the current trend continues
- Gross, operating and net margin
- Bankruptcy risk score and a combined risk level (Low / Medium / High / Critical)
- Liquidity ratios: current ratio, quick ratio, cash ratio and working capital, each explained in plain language
- Payroll check: how many employees, and what average salary, the business can sustain
- Business Health Score (0-100), weighted from profit, margin, cash flow, break-even and risk

**Tests what could go wrong**
- What-if scenarios: prices +10%, sales -20%, product costs +15%

**Tells the owner what to do**
- **Business Doctor:** a ranked list of problems, biggest estimated financial impact first. For example: which product earns too little and what price to move it to, which cost takes too large a share of revenue, whether the business depends on a single supplier
- **Instant price simulation:** apply the suggested prices on the spot and see every number update
- Net profit after income tax, using a rate the user provides

**Saves the results**
- Full text report
- Break-even chart, per-product profitability chart and scenario comparison chart
- A history file, so the next run shows what improved and what got worse compared with the previous one

---

## Design decisions

- **Nothing is guessed.** Tax, VAT and fee rates are always entered by the user. The tool does not assume any country's rules.
- **Itemised input.** Entering products and suppliers one by one is more accurate than a single estimate, and it shows which product carries the business and which one drags it down.
- **Action, not just numbers.** Each problem found comes with a concrete suggestion and an estimated monthly impact.
- **Plain language.** A glossary up front and an explanation next to every ratio.
- **Input validation.** Prices and costs are checked (for example, a product that costs more than it sells for is flagged) and every list can be redone if the user made a mistake.

---

## How to run

The script is interactive (it uses `input()`), so it runs in Google Colab or any Python terminal.

**Google Colab**
1. Open [Google Colab](https://colab.research.google.com/).
2. Paste or upload `business_model_comp.py`.
3. Run it and answer the prompts.

**Locally**
```bash
git clone https://github.com/toniker10/business-financial-diagnostics-tool.git
cd business-financial-diagnostics-tool
pip install matplotlib
python business_model_comp.py
```

**Files created at the end of a run**
- `<name>_financial_report.txt`: the full report
- `<name>_history.json`: results saved for next month's comparison
- `break_even_chart.png`, `product_profitability_chart.png`, `scenario_comparison_chart.png`

---

## Limitations

- It is a simplified planning aid and relies entirely on the numbers the user types in.
- The what-if scenarios change one factor at a time and do not model customer reaction (for example, fewer sales after a price rise).
- The Health Score weights and the risk thresholds are heuristics chosen for this project, not an industry standard.
- Amounts are displayed in one currency (`$`); multi-currency support is not built yet.
- Terminal-only: there is no graphical interface.

## Possible next steps

- Multi-language prompts
- PDF export of the report
- A web or desktop interface
- Multi-currency support

---

## Disclaimer

This tool is a planning aid, not a substitute for professional accounting, tax or financial advice. Confirm important decisions with a licensed accountant or advisor in your country.

## Contributing and license

Suggestions and pull requests are welcome; open an Issue for bugs or ideas. No license has been set yet. Adding a `LICENSE` file (for example MIT) would make the usage terms clear.
